---
title: 作法：將物件資料寫入 XML 檔案 (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: a4fdb496e3b015b2e3b46c9705ba1c05c20423f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595517"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="5e1c3-102">作法：將物件資料寫入 XML 檔案 (C#)</span><span class="sxs-lookup"><span data-stu-id="5e1c3-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="5e1c3-103">此範例會使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e1c3-104">範例</span><span class="sxs-lookup"><span data-stu-id="5e1c3-104">Example</span></span>  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e1c3-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5e1c3-105">Compiling the Code</span></span>  
 <span data-ttu-id="5e1c3-106">此類別必須有不具參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5e1c3-107">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="5e1c3-107">Robust Programming</span></span>  
 <span data-ttu-id="5e1c3-108">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="5e1c3-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5e1c3-109">正在序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="5e1c3-110">該檔案存在且為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5e1c3-111">路徑太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5e1c3-112">磁碟已滿 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5e1c3-113">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="5e1c3-113">.NET Framework Security</span></span>  
 <span data-ttu-id="5e1c3-114">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="5e1c3-115">如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="5e1c3-116">如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="5e1c3-117">若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="5e1c3-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1c3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e1c3-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="5e1c3-119">如何：從 XML 檔案讀取物件資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="5e1c3-119">How to: Read Object Data from an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="5e1c3-120">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="5e1c3-120">Serialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
