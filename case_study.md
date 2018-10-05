## <center>**Case Study**</center>
![figure6](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure6.png)
<center>Figure 6. The sample artifact-centric business process model</center>

![figure7](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure7.png)
<center>Figure 7. The derived workflow net of the artifact-centric business process model in Figure 6</center>

![figure8](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure8.png)
<center>Figure 8. The reachability graph of the derived workflow net in Figure 7</center>


ax^{2} + by^{2} + c = 0

r_1: Customer requests to make an Order o

\[Pre - condition:instate(o,init) \wedge {}^\neg defined(o.orderID) \wedge {}^\neg defined(o.customerName) \wedge {}^\neg defined(o.customerAddress)\]

 Service:createOrder{\rm{ }}\left( o \right)

$Pre - condition:instate(o,add\_order\_item) \wedge defined(o.orderID) \wedge defined(o.customerName) \wedge defined(o.customerAddress)$
