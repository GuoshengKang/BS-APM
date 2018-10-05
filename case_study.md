## <center>**Case Study**</center>
![figure6](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure6.png)
<center>Figure 6. The sample artifact-centric business process model</center>

![figure7](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure7.png)
<center>Figure 7. The derived workflow net of the artifact-centric business process model in Figure 6</center>

![figure8](https://github.com/GuoshengKang/BS-APM/blob/master/images/figure8.png)
<center>Figure 8. The reachability graph of the derived workflow net in Figure 7</center>

<table>
   <tr>
      <td>r_1: Customer requests to make an Order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate (o,init)∧￢defined (o.orderID)∧￢defined (o.customerName)∧￢defined (o.customerAddress)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>createOrder (o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate (o,add_order_item)  ∧defined (o.orderID)∧defined (o.customerName) ∧defined (o.customerAddress)</td>
   </tr>
   <tr>
      <td>r_2: Add items to order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate (o,add_order_item)∧(￢defined(o.grandTotal)⋁(defined(o.grandTotal)∧o.grandTotal>0))∧defined (o.orderID)∧defined (o.customerName) ∧defined (o.customerAddress)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>addItem (o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate (o,add_order_item)∧defined(o.grandTotal)∧o.grandTotal>0</td>
   </tr>
   <tr>
      <td>r_3: Create Shipment s for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate (o,add_order_item)∧instate(s,init)∧defined(o.grandTotal)∧o.grandTotal>0∧￢defined(s.customerName)∧￢defined(s.shippingAddress)∧￢defined(s.shipID)∧￢defined(s.orderID)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>createShipping(s,o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(o,creating_shipping)∧instate(s,waiting_for_ship_item)∧defined(s.customerName)∧defined(s.shippingAddress)∧defined(s.shipID)∧defined(s.orderID)</td>
   </tr>
   <tr>
      <td>r_4: Create Invoice i for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>Instate(i,init)∧instate(o,creating_shipping)∧￢defined(i.invoiceID)∧￢defined(i.orderID)∧￢defined(i.billingAddress)∧￢defined(i.invoiceDate)∧￢defined(i.total)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>createInvoice(i,o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(i,unpaid)∧instate(o,billed) ∧defined(i.invoiceID)∧defined(i.orderID)∧defined(i.billingAddress)∧defined(i.invoiceDate)∧defined(i.total)∧i.total=o.grandTotal</td>
   </tr>
   <tr>
      <td>r_5: Pay for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(o,billed) ∧instate(i,unpaid) ∧defined(i.invoiceID)∧defined(i.orderID)∧defined(i.billingAddress)∧defined(i.invoiceDate)∧defined(i.total)∧i.total=o.grandTotal</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>WeChatPay(i,o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(o,processing_order_item)∧instate(i,paid)∧defined(i.total)∧i.total=o.grandTotal</td>
   </tr>
   <tr>
      <td>r_6: Pay for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(o,billed) ∧instate(i,unpaid) ∧defined(i.invoiceID)∧defined(i.orderID)∧defined(i.billingAddress)∧defined(i.invoiceDate)∧defined(i.total)∧i.total=o.grandTotal</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>Alipay(i,o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(o,processing_order_item)∧instate(i,paid)∧defined(i.total)∧i.total=o.grandTotal</td>
   </tr>
   <tr>
      <td>r_7: prepare ordered items for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(o,processing_order_item)∧instate(i,paid) ∧defined(s.shipping_cost)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>prepareItems(o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(o,processing_complete)</td>
   </tr>
   <tr>
      <td>r_8: pack ordered items for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(o,creating_shipping)∧instate(i,paid)∧instate(s,waiting_for_ship_item)∧defined(s.customerName)∧defined(s.shippingAddress)∧defined(s.shipID)∧defined(s.orderID)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>packItems(s)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(s,ready_for_shipping)</td>
   </tr>
   <tr>
      <td>r_9: load ordered items for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(s,ready_for_shipping) ∧￢defined(s.arrived_station)∧￢defined(s.shipping_cost)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>sf_Express(s)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(s,in_shipping) ∧defined(s.arrived_station)∧defined(s.shipping_cost)</td>
   </tr>
   <tr>
      <td>r_10: load ordered items for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(s,ready_for_shipping)∧￢defined(s.arrived_station)∧￢defined(s.shipping_cost)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>EMS_Express(s)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(s,in_shipping) ∧defined(s.arrived_station)∧defined(s.shipping_cost)</td>
   </tr>
   <tr>
      <td>r_11: ship items for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(s,in_shipping) ∧defined(s.arrived_station)∧￢defined(s.signer)</td>
   </tr>
   <tr>
      <td>Service</td>
      <td>shipItem(s)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(s,shipping_complete) ∧defined(s.signer)</td>
   </tr>
   <tr>
      <td>r_12: close order for order o</td>
   </tr>
   <tr>
      <td>Pre-condition</td>
      <td>instate(o,processing_complete)∧instate(i,paid)∧instate(s,in_shipping) ∧defined(s.signer)  </td>
   </tr>
   <tr>
      <td>Service</td>
      <td>closeOrder(o)</td>
   </tr>
   <tr>
      <td>Post-condition</td>
      <td>instate(o,closed)</td>
   </tr>
   <tr>
      <td></td>
   </tr>
</table>
