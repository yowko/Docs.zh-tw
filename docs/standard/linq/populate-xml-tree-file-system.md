---
title: 如何從檔案系統填入 XML 樹狀結構-LINQ to XML
description: '瞭解如何在 c # 或 Visual Basic 中，從檔案系統填入 XML 樹狀結構。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 6b0307aca9c9075120021967c08efcad8b595653
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552752"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-linq-to-xml"></a>如何從檔案系統填入 XML 樹狀結構 (LINQ to XML) 

XML 樹狀結構的常見且有用的應用，是階層式名稱-值資料存放區。 您可以利用階層式資料填入 XML 樹狀結構，然後進行查詢、轉換，並在必要時，進行序列化。 針對此用途，許多 XML 特定的語義（例如命名空間和空白字元行為）並不重要。 相反地，您是使用 XML 樹狀結構做為小型的記憶體內部單一使用者階層式資料庫。

## <a name="example-populate-an-xml-tree-and-then-query-it"></a>範例：填入 XML 樹狀結構，然後進行查詢

下列範例會使用遞迴來填入 XML 樹狀結構，其中包含本機檔案系統中檔案的相關資料。 然後，它會查詢樹狀結構，總計所有的檔案大小。

```csharp
class Program
{
    static XElement CreateFileSystemXmlTree(string source)
    {
        DirectoryInfo di = new DirectoryInfo(source);
        return new XElement("Dir",
            new XAttribute("Name", di.Name),
            from d in Directory.GetDirectories(source)
            select CreateFileSystemXmlTree(d),
            from fi in di.GetFiles()
            select new XElement("File",
                new XElement("Name", fi.Name),
                new XElement("Length", fi.Length)
            )
        );
    }

    static void Main(string[] args)
    {
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");
        Console.WriteLine(fileSystemTree);
        Console.WriteLine("------");
        long totalFileSize =
            (from f in fileSystemTree.Descendants("File")
             select (long)f.Element("Length")).Sum();
        Console.WriteLine("Total File Size:{0}", totalFileSize);
    }
}
```

```vb
Module Module1
    Function CreateFileSystemXmlTree(ByVal source As String) As XElement
        Dim di As DirectoryInfo = New DirectoryInfo(source)
        Return <Dir Name=<%= di.Name %>>
                   <%= From d In Directory.GetDirectories(source) _
                       Select CreateFileSystemXmlTree(d) %>
                   <%= From fi In di.GetFiles() _
                       Select <File>
                                  <Name><%= fi.Name %></Name>
                                  <Length><%= fi.Length %></Length>
                              </File> %>
               </Dir>
    End Function

    Sub Main()
        Dim fileSystemTree As XElement = CreateFileSystemXmlTree("C:/Tmp")
        Console.WriteLine(fileSystemTree)
        Console.WriteLine("------")
        Dim totalFileSize As Long = _
            ( _
                From f In fileSystemTree...<File> _
                Select CLng(f.<Length>(0)) _
            ).Sum()
        Console.WriteLine("Total File Size:{0}", totalFileSize)
    End Sub
End Module
```

此範例會產生與下列類似的輸出：

```xml
<Dir Name="Tmp">
  <Dir Name="ConsoleApplication1">
    <Dir Name="bin">
      <Dir Name="Debug">
        <File>
          <Name>ConsoleApplication1.exe</Name>
          <Length>4608</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.pdb</Name>
          <Length>11776</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.vshost.exe</Name>
          <Length>9568</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>
          <Length>473</Length>
        </File>
      </Dir>
    </Dir>
    <Dir Name="obj">
      <Dir Name="Debug">
        <Dir Name="TempPE" />
        <File>
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>
          <Length>322</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.exe</Name>
          <Length>4608</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.pdb</Name>
          <Length>11776</Length>
        </File>
      </Dir>
    </Dir>
    <Dir Name="Properties">
      <File>
        <Name>AssemblyInfo.cs</Name>
        <Length>1454</Length>
      </File>
    </Dir>
    <File>
      <Name>ConsoleApplication1.csproj</Name>
      <Length>2546</Length>
    </File>
    <File>
      <Name>ConsoleApplication1.sln</Name>
      <Length>937</Length>
    </File>
    <File>
      <Name>ConsoleApplication1.suo</Name>
      <Length>10752</Length>
    </File>
    <File>
      <Name>Program.cs</Name>
      <Length>269</Length>
    </File>
  </Dir>
</Dir>
------
Total File Size:59089
```
