# Node-RED Flow for Displaying Current Time

This Node-RED flow retrieves the current time for a specific location using the World Clock API and displays it on a dashboard.

## Flow Overview

The flow consists of the following nodes:

1. **Inject Node**: Triggers the flow every 60 seconds.
2. **HTTP Request Node**: Makes a GET request to the World Clock API to retrieve the current time.
3. **Function Node**: Extracts the `datetime` from the API response.
4. **UI Text Node**: Displays the current time on the dashboard.
5. **Debug Nodes**: Used for debugging purposes.

## Nodes Description

### Inject Node

- **ID**: `a5b15f7b38cb5540`
- **Name**: Inject
- **Properties**:
  - **Payload**: Current timestamp
  - **Repeat**: Every 60 seconds

### HTTP Request Node

- **ID**: `f779d284b63416d8`
- **Name**: HTTP Request
- **Method**: GET
- **URL**: `https://api.api-ninjas.com/v1/worldtime?lat=17.9784&lon=79.5941&X-Api-Key=YOUR_API_KEY_HERE`

### Function Node

- **ID**: `bb183230325f47af`
- **Name**: Extract DateTime
- **Function**:
  ```javascript
  var datetime = JSON.parse(msg.payload).datetime;
  msg.payload = datetime;
  return msg;
  ```

### UI Text Node

- **ID**: `801d32b840b8deaf`
- **Name**: Current Time
- **Label**: Current Time
- **Format**: `{{msg.payload}}`
- **Font**: Arial Black
- **Font Size**: 18
- **Color**: #000000

### Debug Nodes

- **ID**: `b7b94f92c58993f8` and `ebfdd74b7c916367`
- **Name**: Debug
- **Purpose**: Display messages in the debug sidebar for troubleshooting.

## Dashboard Configuration

- **UI Group**: Current Time Display
- **UI Tab**: Current Time Display

## How to Use

1. Import the flow into your Node-RED instance.
2. Replace `YOUR_API_KEY_HERE` in the HTTP Request node with your actual API key.
3. Deploy the flow.
4. Open the Node-RED dashboard to see the current time displayed.

## Contact Information

For any questions or support, please contact:

**Keerthi**  
Email: [keerthi.ece.software@gmail.com](mailto:keerthi.ece.software@gmail.com)

## License

This project is licensed under the MIT License.
