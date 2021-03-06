# Feature Summary

When creating emergency kits, we need to provide a starting point. This will be a generic list of items for one person. Types of kits at this time include Home Kit, Go Bag, Car Kit, Work Kit (model this so that the types of kits are extensible). The list of items along with quantity will vary from kit to kit (will be provided to us). 

A Kit shall be identified with a Name and an Icon. (Standard icons for each kit type will be provided)

Once a user creates a Kit (they can create as many as they wish), the basic kit items are added to their list with the appropriate quantities. (See big picture view for calculator functionality when determining quantities). The user will have the ability to add items to this kit, and remove items from this kit.

A Kit item shall include Name, Description, Photo, Expiry Date, Boolean whether the item in the kit is purchased and present in the kit

The user should be able to check an item in their lists as being included in the kit as they purchase supplies. Expiry dates on items also need to be allowed to be entered so that they can be notified when an item needs replacing.

Big Picture View:
In the UI there will be calculator functionality. A user will select to create a type of kit, eg. Home Kit. and enter the number of people and pets in their household. These values are used when creating the user's custom kit to determine quantities for their home/pets.

![image](https://user-images.githubusercontent.com/3979478/101657596-1620c200-3a12-11eb-88e5-f35b8f43bb7c.png)

# Emergency Kit Model
> Note: This is an example of the relationships, please view the API section for implemented structures.
![Emergency Kits Model Diagram](https://github.com/HTBox/TwoWeeksReady/blob/master/assets/models/EmergencyKits.png)

# API

### emergencykits : GET : No parameters
Sample Response:
```json
[
    {
        "id": "db90f019-7cd8-4586-b42b-4dc89a5b21ee",
        "userId": "google-oauth2|127189344966490243983",
        "name": "Test create kit",
        "color": "#FF0000",
        "icon": "mdi-medical-bag",
        "kitItems": []
    }
]
```

### emergencykit-by-id/{id} : GET : id (string)
Sample Response
```json
{
    "id": "db90f019-7cd8-4586-b42b-4dc89a5b21ee",
    "userId": "google-oauth2|127189344966490243983",
    "name": "Test create kit",
    "color": "#FF0000",
    "icon": "mdi-medical-bag",
    "kitItems": []
}
```

### emergencykit-create : POST : No parameters
Sample Request (Body):
```json
{
    "name": "Test create kit",
    "color": "#FF0000",
    "icon": "mdi-medical-bag"
}
```
Sample Response:
```json
{
    "id": "db90f019-7cd8-4586-b42b-4dc89a5b21ee",
    "userId": "google-oauth2|127189344966490243983",
    "name": "Test create kit",
    "color": "#FF0000",
    "icon": "mdi-medical-bag",
    "kitItems": []
}
```
### emergencykit-create-from-base-kit : POST : No Parameters
> Note: This is currently untested in the API
Sample Request (Body):
```json
{
    "baseKitId": "guidvaluehere",
    "name": "My new kit",
    "count": 5
}
```
Sample Response:
```json
{
    "id": "db90f019-7cd8-4586-b42b-4dc89a5b21ee",
    "userId": "google-oauth2|127189344966490243983",
    "name": "Test create kit",
    "color": "#FF0000",
    "icon": "mdi-medical-bag",
    "kitItems": [{
           "id": "someguidvalue",
           "userId": "google-oauth2|127189344966490243983",
           "name": "Item 1",
           "description": "description of item 1",
           "quantity": 5,
           "quantityUnit": "Gallons",
           "photo": "not defined yet",
           "isAvailableInKit": false
          }]
}
```
### emergencykit-update : PUT : No parameters
Sample Request (Body):
```json
{
    "id": "db90f019-7cd8-4586-b42b-4dc89a5b21ee",
    "userId": "google-oauth2|127189344966490243983",
    "name": "Test create kit - UPDATED",
    "color": "#FF0000",
    "icon": "mdi-medical-bag",
    "kitItems": []
}
```
Sample Response:
```json
{
    "id": "db90f019-7cd8-4586-b42b-4dc89a5b21ee",
    "userId": "google-oauth2|127189344966490243983",
    "name": "Test create kit - UPDATED",
    "color": "#FF0000",
    "icon": "mdi-medical-bag",
    "kitItems": []
}
```
### emergencykit-delete/{id} : DELETE : id(string)
Sample Response:
```json
   true
```

### basekits : GET : No parameters
> Note: Untested API (no current base kits defined)
```json
[
  {
     "id": "someguid",
     "name": "Home Kit",
     "icon": "mdi-medical-bag",
     "items": [{
            "id": "someguid",
            "name": "Really helpful item",
            "description": "It's red",
            "photo": "not currently defined yet",
            "quantityPerCount": 5,
            "quantityUnit": "Gallons"
         }]
  }
]
```

# Base Kit Contents

Lists of the ???minimum??? supplies for their respective kits for 1 person or 1 pet:

**Home Kit (2 Weeks Ready kit)**
* ??? Water, 14 gallons
* ??? Water filtration (filter, purification tablets)
* ??? Food, 2 weeks??? worth
* ??? Set of clothing, 5
* ??? Jacket
* ??? Hat and gloves
* ??? Poncho
* ??? Sturdy shoes
* ??? Blanket
* ??? Light source (flashlight, headlamp)
* ??? Extra batteries
* ??? NOAA Weather radio
* ??? Phone charger
* ??? Multi-tool with knife and can opener
* ??? Duct tape
* ??? Crowbar
* ??? Cash, small bills
* ??? First aid kit
* ??? Toiletries (toilet paper, soap, hand sanitizer etc.), 2 weeks??? worth
* ??? Bucket toilet
* ??? Garbage bags
* ??? Personal hygiene items (toothbrush, toothpaste etc.)
* ??? Medications, 2 weeks??? worth
* ??? Face cover/mask, 14
* ??? Medical equipment, 2 weeks??? worth
* ??? Mobility devices
* ??? Glasses/eye care
* ??? Items for children (diapers, wipes, formula, toys etc.)
* ??? Comfort/entertainment
* ??? Copies of important documents (identification, insurance, financial accounts, family records, medical records, pictures etc.)

**Vehicle Kit**
* ??? Water, 3 gallons
* ??? Water filtration (filter, purification tablets)
* ??? Food, 3 days??? worth
* ??? Set of clothing
* ??? Jacket
* ??? Poncho
* ??? Sturdy shoes
* ??? Waterproof blanket
* ??? Light source (flashlight, headlamp)
* ??? Extra batteries
* ??? NOAA Weather radio
* ??? Phone charger
* ??? Multi-tool with knife and can opener
* ??? Duct tape
* ??? Cash, small bills
* ??? First aid kit
* ??? Toiletries (toilet paper, soap, hand sanitizer etc.)
* ??? Medications, 3 days??? worth
* ??? Face cover/mask, 3
* ??? Medical equipment, 3 days??? worth
* ??? Glasses/eye care
* ??? Items for children (diapers, wipes, formula, toys etc.)
* ??? Comfort/entertainment
* ??? Small shovel
* ??? Jumper cables
* ??? Road flare

****Go Kit****
* ??? Water bottle
* ??? Water filtration (filter, purification tablets)
* ??? Food, 3 days??? worth
* ??? Set of clothing
* ??? Jacket
* ??? Poncho
* ??? Sturdy shoes
* ??? Waterproof blanket
* ??? Light source (flashlight, headlamp)
* ??? Extra batteries
* ??? NOAA Weather radio
* ??? Phone charger
* ??? Multi-tool with knife and can opener
* ??? Duct tape
* ??? Cash, small bills
* ??? First aid kit
* ??? Toiletries (toilet paper, soap, hand sanitizer etc.)
* ??? Medications, 3 days??? worth
* ??? Face cover/mask, 3
* ??? Medical equipment, 3 days??? worth
* ??? Glasses/eye care
* ??? Items for children (diapers, wipes, formula, toys etc.)
* ??? Comfort/entertainment
* ??? Copies of important documents (insurance, financial accounts, family records, medical records, pictures etc.)

**Work Kit**
* ??? Water, 3 gallons
* ??? Water filtration (filter, purification tablets)
* ??? Food, 3 days??? worth
* ??? Set of clothing
* ??? Jacket
* ??? Poncho
* ??? Sturdy shoes
* ??? Waterproof blanket
* ??? Light source (flashlight, headlamp)
* ??? Extra batteries
* ??? NOAA Weather radio
* ??? Phone charger
* ??? Multi-tool with knife and can opener
* ??? Cash, small bills
* ??? First aid kit
* ??? Toiletries (toilet paper, soap, hand sanitizer etc.)
* ??? Medications, 3 days??? worth
* ??? Face cover/mask, 3
* ??? Medical equipment, 3 days??? worth
* ??? Glasses/eye care
* ??? Comfort/entertainment
* ??? Copies of important documents (insurance, financial accounts, family records, medical records, pictures etc.)

**Pet Kit**
* ??? Leash or Harness
* ??? Carrier
* ??? Pet Food, 2 weeks??? worth
* ??? Water, 2 weeks??? worth
* ??? Food and water bowls, 2
* ??? Pet waste management supplies (kitty litter, waste sanitation bags etc.)
* ??? Blanket
* ??? Towel
* ??? Photo with family and pets
* ??? Medication
* ??? Medical records
* ??? Toys