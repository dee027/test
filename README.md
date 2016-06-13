# Mastering all your Form needs

## Overview
This CodeLab is all about forms. It will walk you through the fundamentals of Sencha Ext JS forms, the available form field components and various ways of structuring them inside a form. It will also look into loading, saving and validating the form data. 

### What you'll learn?
1. Introduction to forms in Ext JS.
2. What are the different form fields available? 
3. How do we set the field defaults?
4. How do we use the HTML 5 input types?
5. How do we validate form and report to the user?
6. What are the different specialized containers available for form fields?
7. What are the commonly used layouts for form fields?
8. How do we submit the form data?
10. How do we use a model with form?

### What you'll need?
1. [Sencha Cmd 6.x](https://www.sencha.com/products/sencha-cmd/download) 
2. [Sencha Ext JS 6.x SDK](https://www.sencha.com/products/extjs/#overview)
3. [Google Chrome Browser](https://www.google.com/intl/en/chrome/)
4. Text Editor or IDE
5. [XAMPP - Web Server](https://www.apachefriends.org/index.html) - optional


## Environment Setup
**1. Install Sencha Cmd**

   * Open terminal window and type the command `sencha which`. If Cmd is installed, it will show the Sencha Cmd version installed on
     your system. If it is `6.0.1` or above then it is good otherwise,

   	* Type the command `sencha upgrade`. If older version of Cmd is installed, it will start downloading the latest copy. If it
   	  is not installed, it will show you the `command not found` message.  
   	* In case, Cmd is not installed or your firewall prevents you from running the command `sencha upgrade`, you can install the
   	  latest copy of Cmd from <http://www.sencha.com/products/sencha-cmd/download>. Choose the option that includes Java JRE.
   	* After it has been installed by either way, run the command `sencha which` from terminal window. It should now show the
          latest installed Cmd version.
  
**2. Obtain Sencha Ext JS SDK**

 * Downlaod Ext JS 6 SDK from URL <https://www.sencha.com/products/extjs/#overview>.
 * After downloading, unzip the Ext JS SDK at the system root folder.
 * Change the SDK folder's name to  `ext-6`.
	
It should be as follows:
 * Windows: C:/ext-6
 * Mac/UNIX: ~/ext-6

**3. Install Google Chrome**

   * Download and install Chrome from <https://www.google.com/intl/en/chrome/>.
   
**4. Obtain Text Editor or IDE**

   * You can choose the text editor or IDE of your choice.

**5. Install XAMPP**

   * This is optional as Sencha libraries work with any server. 
   * For this session, we will use the Sencha Cmd built-in jetty server.
	
**6. Start the Web server**

   * Start the jetty server by opening the terminal window and typing the following command at `c:/`
     
     `sencha web start`
     
   * After starting the jetty server, you should see the following in terminal window:
     
     ![Jetty Server started](JettyServer.png)
![Jetty Server started](https://github.com/ranjit-battewad/ranjittest/blob/master/JettyServer.png)
![Jetty Server started](https://raw.githubusercontent.com/ranjit-battewad/ranjittest/master/JettyServer.png)
![Jetty Server started](https://github.com/ranjit-battewad/ranjittest/blob/master/JettyServer.png?raw=true)     
   * Leave the terminal window open and running.
     
**7. Test the Server and Ext JS install**

   * Test the install by running URL `localhost:1841` from the browser.
   * You should see the following page: 
   
    ![Ext extracted](https://github.com/walkingtree/codelabs/blob/master/sencha/images/ExtExtracted.png)
![Ext extracted](https://github.com/walkingtree/codelabs/blob/master/ExtExtracted.png)
![Ext extracted](https://raw.githubusercontent.com/walkingtree/codelabs/master/ExtExtracted.png)
![Ext extracted](https://github.com/walkingtree/codelabs/blob/master/ExtExtracted.png?raw=true) 

   * Now click on `ext-6`, you should see the `Welcome to Ext JS 6.0` page.
   
    ![Welcome to Ext JS](https://github.com/walkingtree/codelabs/blob/master/sencha/images/ExtWelcomePage.png)

**NOTE:** If it does not work then you need to review the install instructions and ensure that the server is running.


## Get the starter project
In this section, let us download and extract the starter project for our application.

1. Download `allaboutforms` from [here](https://github.com/walkingtree/codelabs/blob/master/sencha/downloads/allaboutforms.zip?raw=true). Unzip it and place it at `c:/`.	

2. The extracted folder `allaboutforms` contains the starter code for classic version of `MyApp`. It has the following folder structure:
   
   ```javascript
	c:/
		allaboutforms
			app
			overrides
			resources
   ``` 	

3. Open command line and navigate to `c:/ext-6` folder.

4. Generate the `MyApp` application by copying and pasting the following command from `c:/ext-6`:

  ```
   sencha generate app -classic -starter=false MyApp c:/allaboutforms
  ```
  
  This would generate the infrastructure for a classic Ext JS application. The `-starter=false` parameter means starter code is not
  created because you already placed your starter code in the `allaboutforms` folder.
  
5. The first time an application is created, you need to initialize the microloader and create the CSS. To do that, from the terminal
   window, navigate to `c:/allaboutforms` and run the following command:

   ```
   sencha app build development
   ```

6. Open browser and run the application by giving URL `localhost:1841/allaboutforms`. You should see the following screen:

   ![Initial Form Screen](https://github.com/walkingtree/codelabs/blob/master/sencha/images/InitialFormScreen.png)
   
   
### Understand the generated files and folders
* `app/view/forms/Profile.js` - **Profile Form** to demonstrate Form Panel basics.

* `app/view/forms/Application.js` - **Employment Application Form** to be developed in the lab to demonstrate some field components.

* `app/view/forms/BugTracker.js` - **Bug Tracker Form** to be developed in the lab to demonstrate some more field components.

* `app/view/forms/RegistrationForm.js` - **Registration Form** to be developed in the lab to demonstrate use of `inputType`.

* `app/view/forms/ContactForm.js` - **Contact Form** to be developed in the lab to demonstrate form field validations and error
                                    messages.

* `app/view/forms/CheckoutForm.js` -  **Checkout Form** to be developed in the lab to demonstrate Form layouts. 

* `app/view/main/List.js` - **Users** Grid and **Personnel** Grid to be used in the **Grid Editing Form**.

* `app/view/forms/FormLoadRecord.js` - Window with Form to demonstrate loading and submitting of Form data. It gets
                                       created when **Update** button is clicked on the **Users** Grid.

* `app/view/forms/FormModelBinding.js` -  Window to demonstrate using a Model with Form. It gets created when a record is selected in
                                          the **Personnel** Grid.

* `app/model/Country.js`, `app/model/Position.js`,  `app/model/User.js`- Models used by different Stores in the app.

* `resources/data/Country.json`, `resources/data/Position.json`, `resources/data/Users.json`, `resources/data/People.json`- JSON data used by different Stores.

* `app/view/main/MainModel.js` - Main Model to hold bindable data and Stores for the Main View and its child components.

* `app/view/main/MainController.js` - Main Controller to handle events fired on the **Grid Editing Form**.

* `app/view/main/Main.js` - Main View (Viewport) of the application which is a Tab Panel with different Forms as tabs.

## Introduction to Forms
Form Panels are simple panels with additional form handling abilities. They are used in an Ext JS application when there is a need to collect data from the user. 

![Form UML](https://github.com/walkingtree/codelabs/blob/master/sencha/images/FormUML1.png)

Internally, Form Panels work in coordination with an associated object — `Ext.form.Basic` — that handles all of its input field management, validation, submission, and form loading services.

![Flow of control](https://github.com/walkingtree/codelabs/blob/master/sencha/images/FormUML2.png)

Run `MyApp` application from the browser with URL `localhost:1841/allaboutforms` and have a look at **Profile Form**. 

* The UI is `Ext.form.Panel` instance. 
* It has various form field components added as `items`.
* These items are rendered in the form panel in the default `anchor` layout.
* Each form field has a `fieldLabel` property which gives it a label.
* The `emptyText` property shows the default text in an empty field.
* Each form field component also has a `name` and a `value` property. These form the key and value pairs while sending field data
  over the server.
* Two buttons have been added using the `buttons` property.
* The **Send** button calls the form `submit()` method. The `Ext.form.Basic` object gathers data and sends it as a string of
  key-value pairs. (As there is no server side code for this fake URL, it gives 404 error and calls the failure() method.)
* The **Show Field Data** button handler shows the all the fields as name-value pairs.

## Form Fields
Let us have a look at the various form fields available 

![Form Fields Hierarchy](https://github.com/walkingtree/codelabs/blob/master/sencha/images/FormFieldHierarchy.png)

* The name-value pair is provided by the `Ext.form.field.Field` mixin.

* The labeling properties are in the `Ext.form.field.Labelable` mixin

##### Lab 1
Currently the tab **Employee Application Form** just shows an HTML value. Let us create this form using some of the form field
components as shown in the slide below:

![Application Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/ApplicationForm.png)

1. Open class `MyApp.view.forms.Application` in editor. It extends `Ext.form.Panel` with `xtype: 'application'`. We will start adding
   field components by setting the `items` property.
2. Add the combo box for selecting position. For this, copy paste the code below:
   
   ```javascript
        items: [{
	        xtype: 'combo', //Ext.form.field.Combo
	        fieldLabel: 'Which position are you applying for?',
	        labelAlign: 'top', //default is left
	        labelStyle: 'font-weight: bold;',
	        bind: {
	            store: '{positions}'
	        },
	        name: 'position',
	        displayField: 'type',
	        valueField: 'id',
	        queryMode: 'local', // loads local data. Default is remote
	        editable: false, //default is true
	        typeAhead: false, //default is false
	        multiSelect: false, //default is false
	        forceSelection: true //default is 
        }]
  ```
  
  * The `fieldLabel` property provides label for the field.
  * The `labelAlign` property aligns the label with respect to field component. Acceptable values are `left`, `top`, `right`. 
  * The `labelStyle` is a css style string to style the fieldlabels.
  * The `combo` is a store bound component. Its store `positions` is pre-defined in `MyApp.view.main.MainModel` class. The model for   this store is defined in `MyApp.model.Position`class and the json data consumed by this store is in `resources/data/Position`
    file.
  * `queryMode` is the mode in which ComboBox uses the configured store. When `remote`, the ComboBox loads its store dynamically
     based upon user interaction. A parameter containing the typed string is sent in the load request. 

3. Let us add the next few fields now. Copy paste the following code, after the combo config object inside the `items` array.

   ```javascript
	{
		xtype: 'tbtext', //Ext.toolbar.TextItem
		text: 'Are you willing to relaocate?',
		cls: 'font-weight-bold'
	}, {
		xtype: 'radiofield', //Ext.form.field.Radio
		name: 'relocate',
		boxLabel: 'Yes',
		inputValue: 'Y',
		checked: true
	}, {
		xtype: 'radiofield',
		name: 'relocate',
		boxLabel: 'No',
		inputValue: 'N'
	}, {
		xtype: 'datefield', //Ext.form.field.Date
		fieldLabel: 'When can you start?',
		labelAlign: 'top',
		labelStyle: 'font-weight: bold;',
		name: 'doj'
	}, {
		xtype: 'textfield', //Ext.form.field.Text
		name: 'salary',
		fieldLabel: 'Salary Requirements',
		labelAlign: 'top',
		labelStyle: 'font-weight: bold;',
		emptyText: '$',
	}
   ```
   * Only one radio button may be selected based on the `name` property. Use `inputValue` to specify the submitted value, and 
     `boxLabel` to specify the label.
   * Limit the dates via `minDate`, `maxDate`, `disabledDates:[]` and `disableDays:[]`.
   * Use `emptyText` to specify a value seen when the field is empty. Use `submitEmptyText:false` on the form submit to prevent empty
     text values from being submitted.
   
4. Open class `MyApp.view.main.Main` and look at the `items` config object. Replace the second child's `html:'application'` property
   with `xtype:'application'`. Save your work and refresh the application. Click on the **Employment Application Form** tab in the tab panel. You should see the form with configured field components. 

5. Continue adding more items by copying and pasting the following code:

   ```javascript
	{
		xtype: 'htmleditor', //Ext.form.field.HtmlEditor
		fieldLabel: 'Other Details',
		labelAlign: 'top',
		labelStyle: 'font-weight: bold;',
		name: 'details',
		anchor: '60% 40%',
		enableAlignments: true,
		enableColors: true,
		enableFont: true,
		enableFontSize: true,
		enableFormat: true,
		enableLinks: true,
		enableSourceEdit: true
	}, {
		xtype: 'tbtext',
		text: 'Your Contact Information',
		cls: 'font-weight-bold'
	}, {
		xtype: 'textfield',
		fieldLabel: 'First Name',
		name: 'first'
	}, {
		xtype: 'textfield',
		fieldLabel: 'Last Name',
		name: 'last'
	}, {
		xtype: 'textfield',
		fieldLabel: 'Email Address',
		name: 'email',
		emptyText: 'me@somewhere.com'
	}, {
		xtype: 'textfield',
		fieldLabel: 'Phone Number',
		name: 'phone',
		emptyText: 'xxx xxx xxxx'
	}, {
		xtype: 'textareafield', //Ext.form.field.TextArea
		fieldLabel:  'Additional Comments',
		labelAlign: 'top',
		labelStyle: 'font-weight: bold;',
		name: 'comments',
		width: 400,
		height: 100,
		grow: true,
		growMax: 100
	}
   ```
   
  * The default layout for form panel is `anchor`. The `anchor` property here tells the layout as to how the item's width and height
    should be anchored to the container. 
  * All enable properties of `htmleditor` default to true. Set any of them to false to hide the property.
  * The `textareafield` grows in height to fit its content. Use `growMin` and `growMax` to set the minimum and maximum grow heights.

6. Add the **Submit** and **Reset** buttons by pasting the following code after closing the `items` array.

   ```javascript
	buttons: [{
		text: 'Submit',
		handler: function(button) {
			button.up('form').submit({
				url: 'fake.php',
				success: function(form, action) {
					Ext.Msg.alert('Form Saved');
				},
				failure: function(form, action) {
					Ext.Msg.alert('Save Failed');
				}
			});
		}
	}, {
		text: 'Reset',
		handler: function(button) {
			button.up('form').reset();
		}
	}]   
   ```
   
   * The `submit()` method takes a `Ext.form.action.Submit` config. Typically, you specify `url`, and `success` and `failure`
     callbacks. We will talk about it later.
   * The `reset()` method resets the form.

7. Save your work and refresh the app. Enter data and click the **Submit** button. Open Developers Tools and look at the **Network**
   tab. Notice how form data is sent over the server. (It gives 404 error as there is no server side code for this fake url.)

NOTE: In this form, we have used the default `anchor` layout and also added the `scrollable` property to get the scrollbar. But in the next lab, we will use other layouts to structure components nicely inside the panel. 


##### Lab 2
Let us work on the **Bug Tracker Form** now to use some more field components. This form has the following requirements:

![Bug Tracker Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/BugTrackerForm.png)

1. First, we will add some default properties for the fields so that we do not have to configure them on each field object
   individually. For this, open class `MyApp.view.forms.BugTracker` and add the following code:
   
   ```javascript
	fieldDefaults: {
		labelSeparator: ': -', //default is :
		labelStyle: 'font-weight: bold;',
		labelWidth: 120 //default is 100
	}
   ```	
   * The `fieldDefaults` specifies `Ext.form.Labelable` properties to child fields.
   * The `defaults` config can be used to apply default settings to all child items.
   * The `defaultType` can be used to specify a default `xtype` for the child items.
	
2. Add the first two fields `combo` and `htmleditor` by pasting the following code. The combobox uses an inline store for
   demonstration but you can declare it in the ViewModel.

   ```javascript
	items: [{
		xtype: 'combo',
		fieldLabel: 'Tracker',
		emptyText: 'Select',
		name: 'tracker',
		store: ['Bug', 'Feature', 'Development', 'TestCase']
	}, {
		xtype: 'htmleditor',
		fieldLabel: 'Description',
		name: 'desc',
		height: 150 //will occupy the complete width
	}]
   
   ```
 
3. The next 6 fields we want to show in two columns, so we can put them inside a `container` with `column` layout. Add the following
   code inside the `items` array.

   ```javascript
	{
		xtype: 'container',
		layout: 'column',
		defaults: {
			columnWidth: 0.4, //check with 0.33
			padding: '5 30 10 0'
		},
		items: [{
			xtype: 'combo',
			fieldLabel: 'Status',
			emptyText: 'Select',
			name: 'status',
			store: ['New', 'In Progress', 'Completed', 'On Hold']
		}, {
			xtype: 'datefield',
			fieldLabel: 'Start Date',
			name: 'startdate',
			value: new Date() // defaults to today
		}, {
			xtype: 'tagfield', //Ext.form.field.Tag
			fieldLabel: 'Assignee',
			emptyText: 'Select',
			name: 'asgn',
			store: ['Abdul', 'Manish', 'Steven', 'Charu', 'Anil', 'Vikas'],
			growMax: 50
		}, {
			xtype: 'datefield',
			fieldLabel: 'Due Date',
			name: 'duedate'
		}, {
			xtype: 'radiogroup', //Ext.form.RadioGroup
			fieldLabel: 'Priority',
			items: [{
				boxLabel: 'Low',
				name: 'priority',
				inputValue: 1
			}, {
				boxLabel: 'Normal',
				name: 'priority',
				inputValue: 2,
				checked: true
			}, {
				boxLabel: 'High',
				name: 'priority',
				inputValue: 3
			}]
		}, {
			xtype: 'timefield', //Ext.form.field.Time
			fieldLabel: 'Time',
			//minValue: '9:00 AM',
		        //maxValue: '8:00 PM',
		        //increment: 15
		        // format: 'H:i',
		        msgTarget: 'title'
		}]
	}
   ```   
   
   * We have added a `Container` with `column` layout and some `defaults`.
   * Form fields have been added as `items` to this container.
   * The `tagfield` extends combobox with the benefit to allow users to easily add or remove tags from the display value area.
   * The `radiogroup` is a specialized container for arranging radio controls into columns, and provides convenience methods for
     getting, setting, and validating the group of radio buttons as a whole.
   * The `timefield` provides a time input field with a time dropdown and automatic time validation.
   
4. Continue adding more fields to the form by adding this code:

   ```javascript
	{
		xtype: 'slider', //Ext.slider.Single
		fieldLabel: 'Done',
		name: 'done',
		width: 400,
		//vertical: true,
		//height: 200,
		minValue: 0,
		maxValue: 100,
		increment: 10,
		useTips: true, //default is true
		tipText: function(thumb) {
			return Ext.String.format('{0}% complete', thumb.value);
		}
	}, {
		xtype: 'filefield', //Ext.form.field.File
		fieldLabel: 'File',
		name: 'file',
		buttonText: 'Choose File'
	},{
		xtype: 'displayfield',
		value: '(Maximum size: 5 MB)',
		margin: '0 0 0 120'
	},{
		xtype: 'checkboxgroup', //Ext.form.CheckboxGroup
		fieldLabel: 'Watchers',
		columns: 2,
		vertical: true, // true = start with columns, false = start with rows
		items: [{
			boxLabel: 'Alok Ranjan',
			name: 'watcher',
			inputValue: 'AR'
		}, {
			boxLabel: 'Ajit Kumar',
			name: 'watcher',
			inputValue: 'AK'
		}, {
			boxLabel: 'Phani Kiran',
			name: 'watcher',
			inputValue: 'PK'
		}, {
			boxLabel: 'Ranjit Battewad',
			name: 'watcher',
			inputValue: 'RB'
		}]
	},{
		xtype: 'button',
		text: 'Create'
	}
   ```
   
   * The `slider` component can be rendered vertically by setting the `vertical:true` property. The `useTips` and `tipText`
     properties   render custom tips for the slider values. 
   * The  `multislider` component can be used for a slide with multiple thumbs. The `constrainThumbs` property disallows thumbs from
     overlapping each other.
   * The `filefield` file uploads are not performed using normal `Ajax` techniques; see the description for 
     `Ext.form.Basic.hasUpload` for details.
   * The `displayfield` is neither validated nor submitted. It may be useful when you want to display a value from a form's loaded      data but do not want to allow the user to edit or submit that value.
   * The `checkboxgroup` has a specialized layout for arranging checkboxes into columns, and provides convenience methods for
     getting, setting, and validating the group of checkboxes as a whole.

5. Open class `MyApp.view.main.Main` and replace the third child's `html:'bugtracker'` property with `xtype:'bugtracker'`. Save your
   work and refresh the application. Click on the **Bug Tracker Form** tab in the tab panel. You should see this form with configured field components. 

## Using HTML 5 Input Types
`inputType` is the type attribute for input fields -- e.g. radio, text, password, file. Any field may specify `inputType`, which sets the `type` property in the underlying HTML input tag. The extended types supported by HTML5 inputs (url, email, etc.) may also be used.

For example, as there is no separate Ext JS component for password, so the `password` inputType is needed for text fields used as passwords.

**On tablets, the input type determines the keyboard shown to the user.**

Following screenshot shows the different HTML 5 Input Field Types. For tablet support, you might use `email`, `tel` or `url`. The others are rarely used.

![HTML5 Input Field Types](https://github.com/walkingtree/codelabs/blob/master/sencha/images/HTML5InputTypes.png)

**Note:** Use these HTML5 input field types judiciously as some types will use the browser's built-in widget.

### Lab 
In this lab, we will create a **Registration Form** using the HTML5 input types. The form would like this:

![Registration Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/RegistrationForm.png)

1. Open class `MyApp.view.forms.Registration` and add the following code:
   
   ```javascript
	 defaults: {
	        xtype: 'textfield',
	        anchor:'50%',
	        labelWidth: 130
	 },
	 items: [{
	        fieldLabel: 'User Name',
	        name: 'username',
	        emptyText: 'required',
	        allowBlank: false,
	        minLength: 6,
	        maxLength: 12
	 },{
	        fieldLabel: 'Email Address',
	        name: 'email',
	        emptyText: 'me@somewhere.com',
	        inputType: 'email',
	        allowBlank: false
	},{
	        fieldLabel: 'Password',
	        emptyText: 'required',
	        name: 'pwd1',
	        inputType: 'password',
	        allowBlank: false,
	        minLength: 8,
	        maxLength: 12
	},{
	        name: 'pwd2',
	        fieldLabel: 'Repeat Password',
	        inputType: 'password',
	        allowBlank: false,
	},{
	        xtype: 'checkbox',
	        boxLabel: 'I accept the Terms of Use',
	        name: 'acceptTerms'
	}],
	buttons: [{
	        text: 'Register',
	        handler: function() {
	            var form = this.up('form');
                    form.submit({
	                url: 'register.php',
	                success: function(form, action) {
	                   //...
	                },
	                failure: function(form, action) {
	                    //...
	                }
	           });
	       }    
	}]
   ``` 
 
2. Save your work and refresh the application. Try entering the details. The fields will be validated due to the configured
   validations. The password will be masked due to `inputType`. We will talk about validation types later.

## Form Validation
There are validation configs for text fields and number fields. Since these are important base classes, these rules can be used in any sub class field type. 

By default, fields are validated as their value changes or they lose focus due to the following two field properties which are true by default:

* `validateOnChange` 
* `validateOnBlur`
 
### Text Field Validation
For text fields, following are the validations available. Each validation has a default error message which can be changed by their corresponding Validation text.

* Validation: `allowBlank`, `minLength`, `maxLength`, `regex`, `vtype`
* Validation text: `blankText`, `minLengthText`, `maxLengthText`, `regexText`, `vtypeText`

###### Lab 1
Let us add some validations and custom error messages to the **Registration Form**. For this,

1. Open class `MyApp.view.forms.Registration` and replace the **User Name** field object with the following code:
   
   ```javascript
   	{
	        fieldLabel: 'User Name',
	        name: 'username',
	        emptyText: 'required',
	        allowBlank: false,
	        blankText: 'Please type something', //Default: This field is required
	        minLength: 6,
	        minLengthText: 'Too short', // Default: The minimum length for this field is {0}
	        maxLength: 12,
	        maxLengthText: 'Too long' // Default: The maximum length for this field is {0}  
	        regex: /[a-zA-Z]$/,
	        regexText: 'Must be alphabetic' // Defaults to ''         
    }
  ```
  
  * The `allowBlank: false` config will make it a required field and `blankText` would set the corresponding custom message.
  * Similarly, the `minLength` and `maxLength` would set the required length for fields and `minLengthText` and `manLengthText` the
    custom messages.
  * The `regex` validation will restrict the user to enter only alphabetic characters. The `regexText` will show the custom error
    message.
  * Since `validateOnBlur` and `validateOnChange` are true by default, any change in field value or loss of focus, would validate the
    field.

2. Save your work and refresh the app. Try the configured validations.  
  
##### Default Vtype
`Ext.form.field.VTypes` is a singleton that has four predefined validation rules, accessed via the `vtype` configs `alpha`, `alphanum`, `email` or `url`. 

###### Lab 2
Let us add some default and custom Vtype to the `email` and `password` fields. For this,

1. Replace the **Email Address** field with the following:

  ```javascript
  	{
	        fieldLabel: 'Email Address',
	        name: 'email',
	        emptyText: 'me@somewhere.com',
	        inputType: 'email',
	        allowBlank: false,
	        vtype: 'email',
	        vtypeText: 'Please enter your email address'
    }
 ```
2. Save and refresh the app and test the validation on **Email Address** field.

##### Custom Vtype
To create custom VTypes, we can override the `Ext.form.field.VTypes` class and add our own custom VType functions. Once they have been defined, we can use them at application level.

###### Lab 3
We have defined a new VType `password` in an override for `Ext.form.field.VTypes`. Let us see how to use it.

1. Open file `allaboutforms/overrides.VTypes`. It has a custom function `password` which returns true or false based on the validity of `value` argument. It holds the value of field that is being validated. The `passwordText` is the error message that would be displayed in case of invalid field. 

2. Configure this `password` vtype on the **Repeat Password** field as shown below:

   ```javascript
   	{
	        name: 'pwd2',
	        fieldLabel: 'Repeat Password',
	        inputType: 'password',
	        allowBlank: false,
	        vtype: 'password' //custom 
	}
   ```	
3. Save your file and refresh the app. Test both the password fields.

##### Validator
Text fields can have a custom validator function also. If specified, this function will be called first, allowing the developer to override the default validation process.

###### Lab 4
Let us add a validator function here.

1. Replace the **Repeat Password** field wih the following code. We have written a custom vaildator to check whether the passwords
   match or not. It returns true if `value` is true, otherwise returns the error message.

   ```javascript
	{
          name: 'pwd2',
          fieldLabel: 'Repeat Password',
          inputType: 'password',
          allowBlank: false,
          //vtype: 'password'
          validator: function(value) {
            var prev = this.previousSibling('[name=pwd1]');
            return (value === prev.getValue()) ? true : 'Passwords do not match.'
          }
	}
   ```

2. Save your work and refresh the app. Test the password fields.

### Number Field Validation
Number fields have the following validations:

* Validation: `maxValue`, `minValue`
* Validation text: `minText`, `maxText`, `negativeText`, `nanText`

For example,

```javascript
	items: [{
		xtype: 'numberfield',
		fieldLabel: 'numberfield',
		
		value: 11,
		
		maxValue: 10,
		maxText: 'Too high', // Default: The maximum value for this field is {0}
		
		minValue: 1,
		minText: 'Too low', // This is only used if minValue:0
		
		negativeText: 'No', // Default: The value cannot be negative
		
		nanText: 'It is not a number!' // Default: {0} is not a valid number  
	}]
```

## Binding Components to Form State
Any form component with `formBind:true` will be enabled or disabled automatically, depending on whether the form is valid.

##### Lab 
1. In class `MyApp.view.forms.Registration`, add `formBind: true` to the `checkbox` field and `Register` button.
2. Save your work and refresh the app. Both these components will remain disabled till the form is valid.

## Handling Errors Programatically
There are few methods that can be called to handle form validation programatically.

* The `form.isValid()` method returns true or false and as a side effect, shows field error messages. You can also run 
  `isValid()` on an individual field.
* The `form.hasInvalidField()` method returns true or false, but does not invoke field error messages.
* The `getErrors()` method Validates a value according to the field's validation rules and returns an array of errors for any
  failing validations
* The `clearInvalid()` method clears all invalid field messages in this form. It can be called on a form field also.

##### Lab
1. Open class `MyApp.view.forms.Contact` and notice the validations configured on each field.
2. Notice that the handler for **Send** button. It calls the `isValid()` method. If it is false, it calls the `getErrors()` method on
   each field and creates an object with field label and error message.
3. Refresh the app and test the **Contact Form** validations.

## Changing Error Message Location
`msgTarget` specifies the location to display the error messages. Must be one of the following values: 

* `qtip` - Displays a quick tip containing the message when the user hovers over the field. This is the default.
* `title` -  Uses html title attribute.
* `under` -  Shows error message beneath the field.
* `side` -   Adds an error icon to the right of the field, displaying the message in a popup on hover.
* `none` -  Does not display any error message. This might be useful if you are implementing custom error display.
* `[element id]` - Add the error message directly to the innerHTML of the specified element.

##### Lab
![Contact Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/ContactForm.png)

1. Open class `MyApp.view.forms.Contact` and notice the `msgTarget` property configured on each field.
2. Refresh the app and test the location of error messages based on the `msgTarget` property.

## Specialized Form Field Containers
Though the form fields can be placed inside any container with any configured layout but there are some specialized containers available.

* `fieldcontainer`: It is a simple container that includes the `Ext.form.Labelable` mixin and is commonly used for grouping a set of
                    related fields under a single label in a form.

* `fieldset`: A container for grouping sets of fields but may contain any type of components in their items, including other nested
              containers. The default layout for the FieldSet's items is 'anchor', but it can be configured to use any other layout type.

* `radiogroup`: It has a specialized layout for arranging Radio Buttons into columns, and provides convenience methods for getting,
                setting, and validating the group of radio buttons as a whole.

* `checkboxgroup`: It has a specialized layout for arranging Checkboxes into columns, and provides convenience methods for getting,
                   setting, and validating the group of checkboxes as a whole.


## Form Layouts
Forms tend to have complex layouts and nestings. Following are some of the commonly-used layouts:

* `anchor layout`: This is the default form panel layout. In it, the child items are sized relative to the container's dimensions. If
                   the container is resized, all anchored items are automatically re-rendered according to their anchor rules. 

* `form layout`: In it, the items stretch to fill the container width. Also, the labels are automatically sized to match the widest
                 label
* `column layout`: This is another common layout used when creating forms. This layout enables to place fields into two or more
                   columns.

* `hbox layout`: This is also another layout which may be used in form panels or containers within form panels to arrange items
                 horizontally.

* `vbox layout`: Another layout which may be used in form panels is vbox - to arrange items vertically.
 
##### Lab 1
In this section, we will inspect the **Checkout Form** code and see how the items have been arranged inside the form panel.

![Checkout Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/CheckoutForm1.png)

1. Click on the **Checkout Form** tab in the tab panel and have a look at the two fieldsets with titles **Contact Information** and **Mailing Address**. Observe how the fields have been arranged inside them. 
2. Open class `MyApp.view.forms.Checkout` and look at the code. The default layout for the form panel is `anchor`.
3. The `anchor: '100%'` property specifies the width that the item should take up within the container.
4. It has two `fieldset` as items.
5. Some `fieldDefaults` have been configured which apply on both the fieldsets.
6. The `title` config renders as the fieldset's legend.
7. The first `fieldset` with title **Contact Information** has `column` layout which renders items in columns. The number of columns
   depends upon the configured `columnWidth`.
8. The `collapsible` property on the `fieldset` results in a collapse button being rendered next to the legend title.
9. The second `fieldset` with title **Mailing Address** has `form` layout. It stretches items to fill the container width. It also
   sizes the labels match the widest label.
10. The `checkboxToggle` property on `fieldset` renders a checkbox next to title. The `fieldset` will be expanded when the checkbox
    is checked.
11. This `fieldset` has three items - `textfield`, `fieldcontainer` and `combobox`.
12. This nested container `fieldcontainer` has its own `hbox` layout and renders related fields under a single label **City, State,   PIN**.

##### Lab 2
In this section, let us complete this form by adding details for **Billing Address** as shown below. 

Here, we want that if the **Billing Address** is same as **Mailing Address**, then the **Billing Address** fields should be disabled. For this, we have added a `checkbox` which is `checked: true` initially.

The fields get enabled or diabled due to their `disabled` property, which is bound to the `checked` property of the checkbox.

![Checkout Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/CheckoutForm2.png)

1. Open class `MyApp.view.forms.Checkout` and add the following code as third child to the `items` array.

   ```javascript
   	{
		xtype: 'fieldset',
		title: 'Billing Address',
		layout: 'anchor',
		items: [{
			xtype: 'checkbox',
			reference: 'sameAsMail',
			name: 'sameAsMail',
			boxLabel: 'Same as Mailing Address?',
			checked: true,
			margin: '0 0 10 0',
		}, {
			xtype: 'textfield',
			fieldLabel: 'Street Address',
			name: 'streetAdd',
		        bind:{
				disabled: '{sameAsMail.checked}'
			},	
			allowBlank: false,
		}, {
			xtype: 'fieldcontainer',
			fieldLabel: 'City, State, PIN',
			bind:{
				disabled: '{sameAsMail.checked}'
			},
			defaults: {
				xtype: 'textfield',
				margin: '0 10 0 0'
			},
			layout: 'hbox',
			items: [{
				name: 'mailCity',
				emptyText: 'city',
				width: 200,
				allowBlank: false
			}, {
				name: 'mailState',
				emptyText: 'state',
				width: 155,
				allowBlank: false
			}, {
				name: 'mailCode',
				emptyText: 'pin',
				width: 160,
				maskRe: /[\d\-]/,
				regex: /^\d{5}(\-\d{4})?$/,
				regexText: 'Must be in the format xxxxx or xxxxx-xxxx',
				allowBlank: false
			}]
		}, {
			xtype: 'combobox',
			fieldLabel: 'Country',
			name: 'mailCountry',
			maxWidth: 350,
			bind: {
				store: '{countries}',
				disabled: '{sameAsMail.checked}'
			},
			forceSelection: true,
			displayField: 'cntry',
			valueField: 'id',
			typeAhead: true,
			queryMode: 'local',
			allowBlank: false
		}]
	}
   ```
 
2. Save your work and refresh the app to see the complete **Checkout Form**.
  
## Loading and Submitting Form Data

### Submitting by calling the Form submit() method
The `Ext.form.Panel.submit` method sends form data to the back end.

The `submit()` method takes a `Ext.form.action.Submit` config. Typically, you specify `url`, and `success` and `failure` callbacks. The server should respond with a JSON (or XML) packet stating whether the form was successfully processed or not, and any other information you'd like to send to the client.

* Successful Response

  ```javascript
	{
	    success : true, //Boolean - required
	    message : 'Data updated.'
	}
  ```
 
* Success Response with Data

  ```javascript
  	{
	    success : true, //Boolean - required
	    message : 'Data updated.',
	    users: [
	        { "name": "Jean Luc", "email": "jeanluc.picard@enterprise.com", "phone": "555-111-1111" },
	        { "name": "Worf", "email": "worf.moghsson@enterprise.com", "phone": "555-222-2222" },
	        { "name": "Deanna", "email": "deanna.troi@enterprise.com", "phone": "555-333-3333" },
	        { "name": "Data", "email": "mr.data@enterprise.com", "phone": "555-444-4444" }
	   ]
	}
  ```
   
* Failure Response
 
  ```javascript
   	{
	    success : false,
	    message : 'Invalid Operation'
	}
  ```
  
### Loading and Submitting Form Data using a Model
Sometimes you may choose to use a record for validation and data submission. The `Ext.form.Panel` has the following methods which allow to load, update and get the record associated with the form.

* `form.loadRecord(record)` -  loads the form with fields from the record.
* `form.updateRecord()` -  updates the loaded record with form fields. It only updates fields explicitly defined in a record's
                           fields:[].
* `form.getRecord()` - returns the last `Ext.data.Model` instance that was loaded via `loadRecord`.
 
##### Lab 1
In this section, first we will see how we can load a Model into Form, validate it and finally save it using the Model's `save()` method.

Later, we will also see how we can validate a Form and submit it using the Form's `submit()` method.

For this, click on the tab **Grid Editing Form** which shows the following screen:

![Grid Edititng Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/GridEditingForm.png)

1. It shows two grids but we will work on the **Users** grid in this lab. When user selects a record and clicks the **Update** button, it opens a pop-up Window with Form. Our requirement is that the Form should be loaded with the selected record as shown below:

![Grid Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/GridForm1.png)

2. The **Users** grid consumes data from the `users` Store, declared in `MyApp.view.main.MainModel`. This Store holds Models of type
   `MyApp.model.User`. 
   
    ```javascript
        // In 'MyApp.view.main.MainModel'
    	users: {
            model: 'MyApp.model.User',
            autoLoad: true,
            proxy: {
                type: 'ajax',
                url: 'resources/data/Users.json'
            }
        }
   ```
   
   This Model has the following configured validations:
   
   ```javascript
	// In 'MyApp.model.User'
	fields: [{
		name: 'name', 
		type: 'string',
		validators: [{
			type: 'presence',
			message: 'Name is a mandatory field'
		}]
	},{
		name: 'email', 
		type: 'string',
		validators:[{
			type: 'presence',
			message: 'Email is a mandatory field'
		},{
			type: 'email',
			message: 'Email address is not in a valid format'
		}]
	},{
		name: 'phone',
		type: 'string',
		validators:[{
			type: 'format',
			matcher: /^\d{3}-\d{3}-\d{4}$/,
			message: 'Phone Number contains invalid characters'
		}]
	}]
   ```    
   
3. The class `MyApp.view.forms.FormLoadRecord` defines the required Form. On click of the **Update** button in grid, the `onUpdate`
   handler in the `MyApp.view.main.MainController` gets called, which creates an instance of this Window class. 

   ```javascript
	// In 'MyApp.view.main.MainController'
	onUpdate: function(button) {
		var win = Ext.create("MyApp.view.forms.FormLoadRecord", {
			title: 'Edit Form',
			autoShow: true
		});
	}
   ```
   
   This Window class has Form as a child which is added by the following code:
   
   ```javascript
        // In 'MyApp.view.forms.FormLoadRecord'
   	items: [{
		xtype: 'form',
		items: [{
			xtype: 'textfield',
			fieldLabel: 'Name',
			name: 'name',
			allowBlank: false
		}, {
			xtype: 'textfield',
			fieldLabel: 'Email',
			name: 'email',
			allowBlank: false,
			vtype: 'email'
		}, {
			xtype: 'textfield',
			fieldLabel: 'Phone',
			name: 'phone',
			allowBlank: false,
			regex: /^\d{3}-\d{3}-\d{4}$/
		}],
		buttons: [{
			text: 'Model Save',
			handler: 'onModelSave'
		},{
			text: 'Form Submit',
			handler: 'onFormSubmit'
		}]
	}]
   ```   

4. Now, we have to load the selected record (Model) from the grid onto this form. For this, we can call the form's `loadRecord()`
   method. So, replace the `onUpdate` handler definition with the following code:

  ```javascript
  	onUpdate: function(button) {
		var win = Ext.create("MyApp.view.forms.FormLoadRecord", {
			title: 'Edit Form',
		});
		var users = this.lookupReference('userslist');
		var rec = users.getSelection()[0];
		win.down('form').loadRecord(rec);
        	win.show();
	}
  ```
  
  It gets a reference to the **Users** grid, accesses it selected record and loads it into the form.

5. Save your work and refresh the app. Select a record and click the **Update** button. It should load the selected record into the
   form.
6. Next, we want that on click of the form's **Save Model** button, the edited record should first be validated. If valid, it should
   be saved, otherwise it should display some relevant message. This button has the `onModelSave` handler configured. Let's define it by copying and pasting the following code in MainController. 

  ```javascript
	onModelSave: function(button) {
		var form = button.up('form');
		form.updateRecord(); // Only updates what's in the record's fields:[]
		var record = form.getRecord();
		if (record.isValid()) {
			Ext.Msg.alert('Validity', 'The record is valid. Look at network traffic to see what was sent.');
			record.save(); 
		} else {
			Ext.Msg.alert('Validity', 'The record isn\'t valid.');
		}
		button.up('window').close();
	}
  ```
   
   It calls the form's `updateRecord()` method, which updates the Model loaded via `loadRecord()`. 
   
   It then gets this updated record through `getRecord()` method and validates it according to the Model's configured validations, by calling the Model's `isValid()` method. 
   
   If valid, it saves it by calling Model's `save()` method, otherwise prompts the User about Invalid record.

7. Next, we have to handle the form's **Form Submit** button, which is expected to validate a form and submit it. The configured
   handler for this button is `onFormSubmit`. Copy and paste this code in the MainController.

   ```javascript
   	onFormSubmit: function(button) {
		var form = button.up('form');
		if(form.isValid()) {       
			form.submit({
        			url: 'fake.html', //Generates 404 Error but its okay
        			success: function(form, action) {
	                		console.log(action.response);
	                        	button.up('window').close(); 
                		},
	               		failure: function(form, action){
		                        console.log(action.response);
		                        button.up('window').close();
	                	}
			});	
		} else {
        		Ext.Msg.alert('Validity','The record isn\'t valid.');
        	}        	
	}
   ```	

   As this form's fields have some validations configured, the statement `form.isValid()` would validate the form according to those validations. 
   
   If valid, it would call the form's `submit()` method to submit it at the specified `url`. The `success` or `failure` functions would be called based on the received response.	If invalid, it prompts the user about it.
   
   The object passed to the `submit()` method is of `Ext.form.action.Action` type. 
   
8. Save your work and refresh the app. Test the **Form Submit** button.

##### Lab 2
In this lab, we will load the selected record from **Personnel** grid onto the form via Data Binding. We will also validate and save the loaded record. 

Select a record from this grid. It shows a pop-up Window with Form loaded with the selected record, as shown in the screenshot below:

![Grid Form](https://github.com/walkingtree/codelabs/blob/master/sencha/images/GridForm2.png)

1. The **Personnel** grid consumes data from the `people` Store, declared in `MyApp.view.main.MainModel`. This Store holds Models of
   type `MyApp.model.User`. 

   ```javascript
	// In 'MyApp.view.main.MainModel'
	people: {
		model: 'MyApp.model.User',
		autoLoad: true,
		proxy: {
			type: 'ajax',
			url: 'resources/data/People.json'
		}
	}
   ```
   
   The `MyApp.model.User` has the following fields and validators:
   
   ```javascript
   	// In 'MyApp.model.User'
   	fields: [{
	        name: 'name', 
	        type: 'string',
	        validators: [{
	           type: 'presence',
	           message: 'Name is a mandatory field'
	        }]
	},{
	        name: 'email', 
	        type: 'string',
	        validators:[{
	            type: 'presence',
	            message: 'Email is a mandatory field'
	        },{
	            type: 'email',
	            message: 'Email address is not in a valid format'
	        }]
	},{
	        name: 'phone',
	        type: 'string',
	        validators:[{
	            type: 'format',
	            matcher: /^\d{3}-\d{3}-\d{4}$/,
	            message: 'Phone Number contains invalid characters'
	        }]
	 }]
   ```    

2. The grid handles the `select` event through `onItemSelected` handler configured in `MyApp.view.main.MainController`. This handler
   creates an instance of `MyApp.view.forms.FormModelBinding`. While creating its instance, it also passes an inline ViewModel with `editDetails` property which is a reference to the selected record from grid.

   ```javascript
   	// In 'MyApp.view.main.MainController'
	onItemSelected: function(sender, record) {
		Ext.create("MyApp.view.forms.FormModelBinding", {
			viewModel: {
				data: {
					editDetails: record
				}
			},
			title: 'Edit Form',
			autoShow: true
		});
	}
   ```

3. The following code of `MyApp.view.forms.FormModelBinding` class adds Form as a child of Window. Since the `editDetails` property
   of Window's ViewModel (shown above), would be available to Form down the hierarchy, the `bind` property has been used to bind the fields' value to the Model fields. This would automatically load the form fields with the selected Model.

   ```javascript
   	// In 'MyApp.view.forms.FormModelBinding'
	items: [{
		xtype: 'form',
		items: [{
			xtype: 'textfield',
			fieldLabel: 'Name',
			bind: {
				value: '{editDetails.name}'
			}
		}, {
			xtype: 'textfield',
			fieldLabel: 'Email',
			bind: {
				value: '{editDetails.email}'
			}
		}, {
			xtype: 'textfield',
			fieldLabel: 'Phone',
			bind: {
				value: '{editDetails.phone}'
			}

		}],
		buttons: [{
			text: 'Save',
			handler: 'onSave'
		}, {
			text: 'Cancel',
			handler: 'onCancel'
		}]
	}]
   ```

4. Now, let us configure the `modelValidation: true` property on the form panel. This would automatically validate the form fields
   according to Model field validators. For this, open class `MyApp.view.forms.FormModelBinding` and add `modelValidation: true` property to the form object.

5. Let us also bind the **Save** button to the form's state so that it remains disabled till the form is invalid. For this,
   configure `formBind: true` on the **Save** button config object.
 
   ```javascript
   	buttons: [{
		text: 'Save',
		formBind: true,
		handler: 'onSave'
	}, {
		text: 'Cancel',
		handler: 'onCancel'
	}]
   ```
   
6. Save your work and refresh the app. Select a record from **Personnel** grid. Make the **Name** field empty. See that the **Save**
   button gets disabled as the **Name** field has `presence` validator.

7. Next, let's handle the **Save** button which is expected to save the selected Model. In class `MyApp.view.main.MainController`,
   add the following handler:

   ```javascript
   	onSave: function(button) {
		var win = button.up('window');
		var rec = win.getViewModel().get('editDetails');
		rec.commit();
		//rec.save(); There is no back-end code the process the request
		win.close();
	}
   ```
   
   It gets the bound Model `editDetails` and commits it via Model `commit()` method. This would commit all changes made to the bound Model instance. 

8. Let's handle the **Cancel** button which is expected to reject changes made to the selected Model. In class 
   `MyApp.view.main.MainController`, add the following handler:

   ```javascript
	onCancel: function(button) {
		var win = button.up('window');
		win.getViewModel().get('editDetails').reject();
		win.close();
	}
   ```
   
   It gets the bound Model `editDetails` and rejects the changes, by calling the Model's `reject()` method. 

9. Save your work and refresh the app. Test the **Save** and **Cancel** buttons.

## Recap
* Form Panels are simple panels with additional form handling abilities. They are used in an Ext JS application when there is a need to collect data from the user.

* Internally, Form Panels work in coordination with an associated object — `Ext.form.Basic` — that handles all of its input field management, validation, submission, and form loading services.

* Ext JS provides a number of form field components right from basic Textfield to a grid like MultiSelector.

* Each form field component also has a `name` and a `value` property. These form the key and value pairs while sending field data
  over the server.

* The name-value pair is provided by the `Ext.form.field.Field` mixin.

* The labeling properties are in the `Ext.form.field.Labelable` mixin.

* The defaults for fields can be set by:
	 * `defaults` -  to apply default settings to all child items.
	 * `defaultType` - to specify a default `xtype` for the child items.
	 * `fieldDefaults` - to specify `Ext.form.Labelable` properties to child fields.
	 
* Any field may specify `inputType`, which sets the `type` property in the underlying HTML input tag. The extended types supported by HTML5 inputs (url, email, etc.) may also be used.

* By default, fields are validated as their value changes or they lose focus. 

* For text fields, the validations are - 

	* Validation: `allowBlank`, `minLength`, `maxLength`, `regex`, `vtype`
	* Validation text: `blankText`, `minLengthText`, `maxLengthText`, `regexText`, `vtypeText`
	* validator function.

* Number fields have the following validations:

	* Validation: `maxValue`, `minValue`
	* Validation text: `minText`, `maxText`, `negativeText`, `nanText`
	
* Any form component can be enabled or disabled automatically, depending on whether the form is valid or inavalid, by setting the  `formBind:true` property.  

* There are few methods that can be called to handle form validation programatically.

	* The `form.isValid()` method returns true or false and shows field error messages. You can also run 
	  `isValid()` on an individual field.
	* The `form.hasInvalidField()` method returns true or false, but does not invoke field error messages.
	* The `clearInvalid()` method clears all invalid field messages in this form. It can be called on a form field also.
	* The `reset()` method resets the form fields' values. 

* The location to display the error messages can be changed by setting the `msgTarget` property. It can have ony of the following values:

	* `qtip` - Displays a quick tip containing the message when the user hovers over the field. This is the default.
	* `title` -  Uses html title attribute.
	* `under` -  Shows error message beneath the field.
	* `side` -   Adds an error icon to the right of the field, displaying the message in a popup on hover.
	* `none` -  Don't display any error message. This might be useful if you are implementing custom error display.
	* `[element id]` - Add the error message directly to the innerHTML of the specified element.

* There are some specialized containers for form fields - `fieldcontainer`, `fieldset`, `radiogroup` and `checkboxgroup`.

* Some commonly-used layouts for forms are: `anchor` (default), `form`, `column`, `hbox` and `vbox`.

* The form data can be loaded or submitted by any of the following ways:
	
	* Form's submit() method:
	
		* It sends form data to the back end.
		* It takes a `Ext.form.action.Submit` config and the server should respond with a JSON (or XML) packet stating whether the form was successfully processed or not, and any other information you'd like to send to the client.
	
			* Successful Response
				
				```javascript
					{
						success : true, //Boolean - required
						message : 'Data updated.'
					}
				```
				 
			* Success Response with Data
			
				  ```javascript
				  	{
						 success : true, //Boolean - required
						 message : 'Data updated.',
						 users: [
						         { "name": "Jean Luc" },
						         { "name": "Worf" },
						         { "name": "Deanna"},
						         { "name": "Data" }
						 ]
					}
				  ```
			   
			* Failure Response
			 
				  ```javascript
				   	{
					    success : false,
					    message : 'Invalid Operation'
					}
				  ```
  
	* Loading and Submitting using a Model
		* Sometimes you may choose to use a Model (record) for validation and data submission. The `Ext.form.Panel` has the following methods which allow to load, update and get the record associated with the form.
		
		* `form.loadRecord(record)` -  updates the form with fields from the record.
		* `form.updateRecord()` -  updates the loaded record with form fields. It only updates fields explicitly defined in a
		record's fields:[].
		* `form.getRecord()` - returns the last `Ext.data.Model` instance that was loaded via `loadRecord`.




 
  
  
