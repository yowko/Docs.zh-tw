---
title: "如何：從 XML 檔案讀取物件資料 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a3389de2f3272a546a7380ef386f5d88666e6d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="5cdcb-102">如何：從 XML 檔案讀取物件資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="5cdcb-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="5cdcb-103">此範例會讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cdcb-104">範例</span><span class="sxs-lookup"><span data-stu-id="5cdcb-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cdcb-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5cdcb-105">Compiling the Code</span></span>  
 <span data-ttu-id="5cdcb-106">以內含序列化資料之檔案的名稱取代檔案名稱 "c:\temp\SerializationOverview.xml"。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="5cdcb-107">如需序列化資料的詳細資訊，請參閱[如何：將物件資料寫入 XML 檔案 (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="5cdcb-108">此類別必須有不具參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="5cdcb-109">只會還原序列化公用屬性和欄位。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5cdcb-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="5cdcb-110">Robust Programming</span></span>  
 <span data-ttu-id="5cdcb-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="5cdcb-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5cdcb-112">正在序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="5cdcb-113">檔案中的資料不是來自要還原序列化之類別的資料。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="5cdcb-114">檔案不存在 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5cdcb-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="5cdcb-115">.NET Framework Security</span></span>  
 <span data-ttu-id="5cdcb-116">永遠會驗證輸入，而且絕不會還原序列化來自未受信任來源的資料。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="5cdcb-117">重新建立的物件會以還原序列化該物件之程式碼的權限，在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="5cdcb-118">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="5cdcb-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdcb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cdcb-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="5cdcb-120">如何：將物件資料寫入到 XML 檔案 (C#)</span><span class="sxs-lookup"><span data-stu-id="5cdcb-120">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="5cdcb-121">序列化 (C# )</span><span class="sxs-lookup"><span data-stu-id="5cdcb-121">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="5cdcb-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5cdcb-122">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
