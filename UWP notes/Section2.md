# Data and Asynchronous Tasks

## Intro

1. FileIO has functions for handling File inputs like String reading etc
2. Talks about async await
3. FileOpenerPicker
   1. ViewMode(Thumbnail,list etc)
   2. SuggestedStartLocation
   3. FiletypeFilter
   4. PickSingleFileAsync()
4. FolderPicker
   1. SuggestedStartLocation
   2. FilterTypeFilter
   3. PickSingleFolderAsync()
5. Folder
   1. GetFileAsync();
6. Cancellation token can be added using CancellationTokenSource.

## Making REST Calls

1. HttpClient
   1. GetStringAsync("URL")
   2. DefaultRequestHeaders
   3. GetAsync
      1. Response.Content.ReadStringAsync()
      2. also others
   4. About XML parsing
      1. xml = XElement.Parse(Text)
   5. About JSON parsing
      1. Built in
         1. DataContractJsonSerializer(type)
         2. ReadObject(stream)
      2. NewtonSoft
         1. JsonConvert.DeserializeObject&lt;type&gt;(Text)
   6. REST Operations
      1. POST
      2. GET
      3. PUT
      4. DELETE

## Local database

1. Windows.Current.Local
   1. C:\Users\pushparaj-pt2374\AppData\Local\Packages\GUID\LocalState
2. Setup
   1. SDK -> SQLite for Universal Windows Platform
   2. Add reference
      1. SQLite for Universal Windows Platform
      2. Visual C++ 2015 Runtime for Universal Windows Platform
   3. Nuget
      1. SQLite.Net-PCL 
3. SQLite.net
   1. Annotations
      1. [PrimaryKey]
   2. OpenOrRecreateConnection
      1. Filename .sqlite
      2. local folder
      3. new SQLiteConnection(new SQLite.Net.Platform.WinRT.SQLitePlatformwinRT(),path) -> returns SQLiteConnection
   3. con.CreateTable<ModelClass>();
   4. conn.InsertOrReplace(Object) -> this uses primary key annotation to replace
   5. conn.Table<Model> select p and other Linq syntactic sugars

## Use Threading

1. Task
   1. Use await Task.Run(function() => {});
   2. Use Windows.ApplicationModel.Core.CoreApplication.MainView.CoreWindow.Dispatcher.Run(function()=>{});
