# CWC-7
# CWC-7
Team no.-7
Team members:
1.Pranjal More
2.Ketaki Kshirsagar
3.Gayatri Chaudhari
4.Akanksha Kulkarni
------------------------------------------------------------------------------
To design the OHLC Engine we have used javascript,html and css.To create the dashboard we have used javascript,html and css.
Javascript makes it easier to create visualizations and charts with it's numerous charting options and many charting libraries.
 Here we are using the Anychart JS library.
Firstly we have created a HTML page for the ohlc chart.
We have imported the AnyChart's core and stock modules and the input is taken from the json file provided.
We have used data table to load the data and methods such as loadJsonFile(),addData(),plot(),stock(),ohlc(),etc

Solution:
The given solution can be run on VSCode.

<!DOCTYPE html>
<html>
 <head>
  <title>OHLC Engine</title>
   <script src="https://cdn.anychart.com/releases/8.10.0/js/anychart-core.min.js"></script>
   <script src="https://cdn.anychart.com/releases/8.10.0/js/anychart-stock.min.js"></script>
   <script src="https://cdn.anychart.com/releases/8.10.0/js/anychart-data-adapter.min.js"></script>
   <style type="text/css">html,body,#chart{
    width:100%;height:100%;margin:0%;padding:0%;
  }</style>
</head>
<body>
  <div id="chart"></div>
  <script>
    anychart.onDocumentReady(function (data){
    anychart.data.loadJsonFile("C:\Users\Manoj\Downloads\Stock List.json", function (stockdata) {
      var dataTable =anychart.data.table();
      dataTable.addData(data);
      //mapping
      var mapping=dataTable.mapAs({close:1,
        high:2,
        low:3,
        open:4});
      var chart=anychart.stock();   // creating stock chart
      var plot=chart.plot(0);       //creating first plot on the chart
      plot                         //creating the ohlc series
        .ohlc()
        .data(mapping)
        .name('AAPL');    
      plot                        //defining grid settings
        .yGrid(true)
        .xGrid(true)
        .yMinorGrid(true)
        .xMinorGrid(true);
      chart.scroller().area(dataTable.mapAs({value:4}));   //scroller series allows a closer look at a specified range of data
      chart.title('OHLC Engine');    //set the chart title
      chart.container('chart');
      chart.draw();   //draw chart
      })
    })         
  </script>
</body>
</html>

path=file:///C:/Users/Manoj/Downloads/Hackathon.html
