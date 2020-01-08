---
title: 如何從 XML 檔案讀取物件資料（C#）
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 2da5919c11ed2d6e43f4f9fc406f43e3ed48060f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346426"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="1ea4d-102">如何從 XML 檔案讀取物件資料（C#）</span><span class="sxs-lookup"><span data-stu-id="1ea4d-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="1ea4d-103">此範例會讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ea4d-104">範例</span><span class="sxs-lookup"><span data-stu-id="1ea4d-104">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1ea4d-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1ea4d-105">Compiling the Code</span></span>  
<span data-ttu-id="1ea4d-106">以內含序列化資料之檔案的名稱取代檔案名稱 "c:\temp\SerializationOverview.xml"。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="1ea4d-107">如需序列化資料的詳細資訊，請參閱[如何將物件資料寫入 XML 檔案（C#）](./how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="1ea4d-108">此類別必須有不具參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="1ea4d-109">只會還原序列化公用屬性和欄位。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1ea4d-110">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="1ea4d-110">Robust Programming</span></span>  
 <span data-ttu-id="1ea4d-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="1ea4d-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1ea4d-112">正在序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="1ea4d-113">檔案中的資料不是來自要還原序列化之類別的資料。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="1ea4d-114">檔案不存在 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1ea4d-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1ea4d-115">.NET Framework Security</span></span>  
 <span data-ttu-id="1ea4d-116">永遠會驗證輸入，而且絕不會還原序列化來自未受信任來源的資料。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="1ea4d-117">重新建立的物件會以還原序列化該物件之程式碼的權限，在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="1ea4d-118">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="1ea4d-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea4d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea4d-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="1ea4d-120">如何將物件資料寫入 XML 檔案（C#）</span><span class="sxs-lookup"><span data-stu-id="1ea4d-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="1ea4d-121">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="1ea4d-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="1ea4d-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1ea4d-122">C# Programming Guide</span></span>](../../index.md)
