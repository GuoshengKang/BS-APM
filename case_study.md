## <center>**Case Study**</center>
![figure6](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure6.png)
<center>Figure 6. The sample artifact-centric business process model</center>

![figure7](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure7.png)
<center>Figure 7. The derived workflow net of the artifact-centric business process model in Figure 6</center>

![figure8](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure8.png)
<center>Figure 8. The reachability graph of the derived workflow net in Figure 7</center>


r_1: Customer requests to make an Order o

<img src="http://chart.googleapis.com/chart?cht=tx&chl=  \[Pre - condition:instate(o,init) \wedge {}^\neg defined(o.orderID) \wedge {}^\neg defined(o.customerName) \wedge {}^\neg defined(o.customerAddress)\]">

<img src="http://chart.googleapis.com/chart?cht=tx&chl=  \[Service:createOrder{\rm{ }}\left( o \right)\]">

<img src="http://chart.googleapis.com/chart?cht=tx&chl=  \[Pre - condition:instate(o,add\_order\_item) \wedge defined(o.orderID) \wedge defined(o.customerName) \wedge defined(o.customerAddress)\]">
