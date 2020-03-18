---
title: 如何資料流具有標頭資訊 （C#） 存取權限的 XML 片段
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712386"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>如何資料流具有標頭資訊 （C#） 存取權限的 XML 片段
有時候您必須讀取任意大的 XML 檔案並撰寫您的應用程式，讓應用程式的記憶體使用量可以預測。 如果您嘗試使用大型 XML 檔案填入 XML 樹狀結構，您的記憶體使用量將與檔案大小成正比，也就是，變成過度。 因此，您應該改用資料流技術。  
  
其中一個選項是使用 <xref:System.Xml.XmlReader> 撰寫您的應用程式。 但是，您可能希望使用 LINQ 查詢 XML 樹。 若發生這種情況，您可以撰寫自己的自訂座標軸方法。 有關詳細資訊，請參閱[如何編寫 LINQ 到 XML 軸方法 （C#）。](./how-to-write-a-linq-to-xml-axis-method.md)
  
 若要撰寫您自己的座標軸方法，您可以撰寫使用 <xref:System.Xml.XmlReader> 讀取節點的小方法，直到該方法到達您感興趣的其中一個節點。 然後，該方法會呼叫從 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 讀取的 <xref:System.Xml.XmlReader>，並具現化 XML 片段。 接著，它會針對列舉自訂座標軸方法的方法，透過 `yield return` 產生每個片段。 此時，您就可以在自訂座標軸方法上撰寫 LINQ 查詢。  
  
 在您僅需要處理一次來源文件的情況下，最適合使用資料流技術，而且您可以用文件的順序處理項目。 特定的標準查詢運算子 (例如，<xref:System.Linq.Enumerable.OrderBy%2A>) 會反覆查看其來源、收集所有資料、排序這些資料，最後產生順序中的第一個項目。 如果使用在生成第一個項之前實現其源的查詢運算子，則不會保留較小的記憶體佔用空間。  
  
## <a name="example"></a>範例  

有時候問題會變得更有趣。 在下列 XML 文件中，您自訂座標軸方法的消費者也必須知道每個項目所屬客戶的名稱。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 這個範例所採取的方法也是監看這個標頭資訊、儲存標頭資訊，然後建置同時包含您所列舉之標頭資訊與細節的小型 XML 樹狀結構。 這個座標軸方法接著就會產生這個新的小型 XML 樹狀結構。 該查詢將可以存取標頭資訊以及詳細資訊。  
  
 此方法擁有小的記憶體使用量。 產生每個細節 XML 片段時，不會針對上一個片段保留任何參考，而且這個片段適用於記憶體回收。 此技術在堆上創建許多短壽命物件。  
  
 下列範例顯示如何實作與使用從 URI 指定之檔案資料流 XML 片段的自訂座標軸方法。 此自訂`Customer`軸的編寫方式是，它期望文檔具有 和`Name``Item`元素，並且這些元素將像在上面`Source.xml`的文檔中一樣排列。 這是簡化的實作方法。 較為複雜的實作方法則用於剖析無效的文件。  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 此程式碼會產生下列輸出：  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
