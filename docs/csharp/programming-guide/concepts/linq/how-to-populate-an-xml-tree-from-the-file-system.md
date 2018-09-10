---
title: 如何：從檔案系統填入 XML 樹狀結構 (C#)
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 7bddab1942c5a673969e271338f17705914f81a4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204990"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="70c35-102">如何：從檔案系統填入 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="70c35-102">How to: Populate an XML Tree from the File System (C#)</span></span>
<span data-ttu-id="70c35-103">XML 樹狀的常用與實用應用為當做階層式名稱/值資料存放區使用。</span><span class="sxs-lookup"><span data-stu-id="70c35-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="70c35-104">您可以利用階層式資料填入 XML 樹狀結構，然後進行查詢、轉換，並在必要時，進行序列化。</span><span class="sxs-lookup"><span data-stu-id="70c35-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="70c35-105">在這個使用案例中，許多 XML 專用語意 (Semantics) (例如，命名空間與空白字元行為) 都不重要。</span><span class="sxs-lookup"><span data-stu-id="70c35-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="70c35-106">反之，您會使用 XML 樹狀當做記憶體中的小型單一使用者階層式資料庫。</span><span class="sxs-lookup"><span data-stu-id="70c35-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70c35-107">範例</span><span class="sxs-lookup"><span data-stu-id="70c35-107">Example</span></span>  
 <span data-ttu-id="70c35-108">下列範例會使用遞迴，從本機檔案系統填入 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="70c35-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="70c35-109">接著，它會查詢樹狀結構，計算樹狀結構中，所有檔案大小的總數。</span><span class="sxs-lookup"><span data-stu-id="70c35-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
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
  
 <span data-ttu-id="70c35-110">此範例會產生與下列類似的輸出：</span><span class="sxs-lookup"><span data-stu-id="70c35-110">This example produces output similar to the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70c35-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="70c35-111">See Also</span></span>

- [<span data-ttu-id="70c35-112">進階查詢技術 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="70c35-112">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
