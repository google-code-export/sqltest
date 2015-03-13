<?xml version="1.0" encoding="utf-8"?>
<mx:Application width="600"
> height="400"
> xmlns:mx="http://www.adobe.com/2006/mxml"
> xmlns:as3flexdb="phi.framework.sql.**"
> layout="vertical">**

> 

&lt;mx:Button label="Get Users" click="st1.execute()"/&gt;



> 

&lt;mx:DataGrid id="dg1" dataProvider="{users}"&gt;


> > 

&lt;mx:columns&gt;


> > > 

&lt;mx:DataGridColumn headerText="#ID" dataField="idUser" /&gt;


> > > 

&lt;mx:DataGridColumn headerText="Username" dataField="username" /&gt;


> > > 

&lt;mx:DataGridColumn headerText="Password" dataField="password" /&gt;



> > 

&lt;/mx:columns&gt;



> 

&lt;/mx:DataGrid&gt;



> <!-- ++++++++++++++++++++++++++++ -->
> <!-- AS3FlexDB code -->

> 

&lt;as3flexdb:MySQLAdapter id="defaultAdapter" host="localhost" database="dbtest"/&gt;


> 

&lt;as3flexdb:SQLConnection id="conn1" sqlAdapter="{defaultAdapter}"/&gt;



> <as3flexdb:SQLStatement id="st1"
> > sqlConnection="{conn1}"
> > text="SELECT **FROM users WHERE 1"
> > sqlResult="sqlResultHandler(event)"
> > sqlError="sqlErrorHandler(event)"/>**


> 

&lt;mx:Script&gt;


> > <![CDATA[


> import phi.framework.sql.**;
> import mx.collections.ArrayCollection;**


> [Bindable](Bindable.md)
> protected var users :ArrayCollection = new ArrayCollection();

> protected function sqlResultHandler(event:SQLEvent):void
> {
> > var result :SQLResult = event.result;


> users.removeAll();

> // trace result
> for each( var item :Object in result.data )
> > users.addItem( item );

> }


> protected function sqlErrorHandler(event:SQLErrorEvent):void
> {
> > trace( event.error );

> }

> ]]>
> 

&lt;/mx:Script&gt;




Unknown end tag for &lt;/Application&gt;

