# Create-outstanding-dashboards-with-the-new-semantic.dashboard-package

The details of the codeset and plots are included in the attached Microsoft Word Document (.docx) file in this repository. 
You need to view the file in "Read Mode" to see the contents properly after downloading the same.

Dashboard with Semantic UI Support for Shiny.Are you fed up with ordinary shinydashboard look?Give your app a new fresh look with Fomantic UI support.

    library(shiny)
    library(shinydashboard) # <-- Change this line to: library(semantic.dashboard)

    ui <- dashboardPage(
      dashboardHeader(title = "Basic dashboard"),
      dashboardSidebar(sidebarMenu(
          menuItem(tabName = "home", text = "Home", icon = icon("home")),
          menuItem(tabName = "another", text = "Another Tab", icon = icon("heart"))
      )),
      dashboardBody(
        fluidRow(
          box(plotOutput("plot1", height = 250)),
          box(
            title = "Controls",
            sliderInput("slider", "Number of observations:", 1, 100, 50)
          )
        )
      )
    )

    server <- function(input, output) {
      set.seed(122)
      histdata <- rnorm(500)
      output$plot1 <- renderPlot({
        data <- histdata[seq_len(input$slider)]
        hist(data)
      })
    }

shinyApp(ui, server)

![image](https://user-images.githubusercontent.com/26252963/148494869-bda9d235-c7a2-4b23-af57-f5063ac1cd30.png)

