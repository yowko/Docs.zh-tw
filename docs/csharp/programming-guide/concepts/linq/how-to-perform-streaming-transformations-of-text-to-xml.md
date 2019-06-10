---
title: 作法：執行文字到 XML 的串流轉換 (C#)
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: d37ea5167576098d4ea343e49ae4ff6bac20d4ba
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485241"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>作法：執行文字到 XML 的串流轉換 (C#)
處理文字檔的其中一個方法是撰寫擴充方法，該方法會使用 `yield return` 建構將文字檔一次串流一行。 然後您可以撰寫利用延後的方式處理文字檔的 LINQ 查詢。 如果您接著使用 <xref:System.Xml.Linq.XStreamingElement> 串流輸出，您就可以使用最少量的記憶體建立文字檔到 XML 的轉換，而不必在乎來源文字檔的大小。  
  
 關於串流轉換有一些警告。 在您可以處理一次整個檔案的情況下，以及您可以用行出現在來源文件中的順序處理這些行時，最適合使用串流轉換。 如果您必須多次處理檔案，或者，如果您必須在處理檔案前排序行，您將會失去使用串流技術的好處。  
  
## <a name="example"></a>範例  
 下列文字檔 People.txt 為這個範例的來源。  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 下列程式碼包含的擴充方法可以用延緩的方式，串流文字檔的行。  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XStreamingElement>
