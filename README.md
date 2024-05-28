# Partnerize S2S (Server to Server) Tracking Tag
This tag template incorporates a Click event and a Conversion event.
## Click Event
This tag should be "`PageView`" as the type, as we want this to fire on all landing pages when the page loads. It allows you to specify the length of the httpOnly cookie that gets created, as well as which URL parameter to look for the click_reference in. This will create the usual "partnerizeClickReference" cookie with the life-span set here. This should fire on all pages, and take into consideration any conditional logic you would have (cookie consent, attribution, etc.)
## Conversion Event
We will need the conversion data sent to us, so another tag must be created for this.
### Item Details
If you have items, provide the "Variable" that contains the items, and we will perform the standard mapping options:
```
switch (property) {
  case 'currency':
    break;
    
  case 'sku':
  case 'id':
  case 'item_id':
  case 'item_sku':
    requestUrl += '/sku:' + getPropertyValue(data.itemArray[i][property]);
    break;

  case 'category':
  case 'item_category':
    requestUrl += '/category:' + getPropertyValue(data.itemArray[i][property]);
    break;

  case 'price':
    requestUrl += '/value:' + getPropertyValue(data.itemArray[i][property]);
    break;

  default:
    requestUrl += '/' + formatParameter(property) + ':' + getPropertyValue(data.itemArray[i][property]);
    break;
}
```

