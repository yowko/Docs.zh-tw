---
title: '如何從 XML 檔案讀取物件資料 (c # ) '
description: '這個 c # 範例會讀取先前使用 XmlSerializer 類別寫入至 XML 檔案的物件資料。'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 8d607424201cfad08df1c5ffbfb66a114b31886d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178758"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="bc2ff-103">如何從 XML 檔案讀取物件資料 (c # ) </span><span class="sxs-lookup"><span data-stu-id="bc2ff-103">How to read object data from an XML file (C#)</span></span>

<span data-ttu-id="bc2ff-104">此範例會讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc2ff-105">範例</span><span class="sxs-lookup"><span data-stu-id="bc2ff-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc2ff-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bc2ff-106">Compiling the Code</span></span>  

<span data-ttu-id="bc2ff-107">以內含序列化資料之檔案的名稱取代檔案名稱 "c:\temp\SerializationOverview.xml"。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="bc2ff-108">如需序列化資料的詳細資訊，請參閱 [如何將物件資料寫入 XML 檔案 (c # ) ](./how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-108">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="bc2ff-109">此類別必須有不具參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="bc2ff-110">只會還原序列化公用屬性和欄位。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bc2ff-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="bc2ff-111">Robust Programming</span></span>  

 <span data-ttu-id="bc2ff-112">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="bc2ff-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="bc2ff-113">正在序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="bc2ff-114">檔案中的資料不是來自要還原序列化之類別的資料。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="bc2ff-115">檔案不存在 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="bc2ff-116">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="bc2ff-116">.NET Security</span></span>  

 <span data-ttu-id="bc2ff-117">永遠會驗證輸入，而且絕不會還原序列化來自未受信任來源的資料。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="bc2ff-118">重新建立的物件會以還原序列化該物件之程式碼的權限，在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="bc2ff-119">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="bc2ff-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2ff-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc2ff-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="bc2ff-121">如何將物件資料寫入 XML 檔案 (c # ) </span><span class="sxs-lookup"><span data-stu-id="bc2ff-121">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="bc2ff-122">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc2ff-122">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="bc2ff-123">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bc2ff-123">C# Programming Guide</span></span>](../../index.md)
