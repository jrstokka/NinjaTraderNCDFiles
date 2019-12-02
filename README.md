# NinjaTraderNCDFiles
Classes to read NinjaTrader proprietary NCD Files.

## How to use the classes...

### 1) Set the static value for the Directory containing the NinjaTrader data.

This path designation tells the helper classes which directories in which to search for the NinjaTrader files.

As of the publish date NT8 files are found by default in 
{driveletter}:\Users\{yourusername}\Documents\NinjaTrader 8\db

```csharp
NinjaTrader.GlobalOptions.HistoricalDataPath = $"{driveletter}:\Users\{yourusername}\Documents\NinjaTrader 8\db";
```

### 2) Create the Helperobject...

```csharp
DateTime startDateTime = new DateTime.ParseExact("092719", "MMddyy", CultureInfo.InvariantCulture);
int numberDaysForward = 7;
int numberDaysBack = 7;
NCDFiles myFiles = new NCDFiles(NCDFileType.Minute, "AAPL", startDateTime, numberDaysForward, numberDaysBack);
```

### 3) Process the files...

```csharp
while (!myFiles.EndOfData)
{
  MinuteRecord record = myFiles.ReadNextRecord();
  // do whatever you want with it
}
```

This example is for Minute files.  If you are processing Tick files then simply make the appropriate changes in the constructor and reader...

```csharp
NCDFiles myFiles = new NCDFiles(NCDFileType.Minute, "AAPL", startDateTime, numberDaysForward, numberDaysBack);
while (!myFiles.EndOfData)
{
  TickRecord record = myFiles.ReadNextRecord();
}
```

Feel free to reach out to me directly if you have any questions or comments or would like any custom libraries developed that utilize the files.

Enjoy!

jrstokka gmail or skype jrstokka
