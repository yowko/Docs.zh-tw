---
title: HOW TO：將物件資料寫入至 XML 檔案 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 17f8463a4b905028d37a2e005562867f87f4bd2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624353"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="823ce-102">HOW TO：將物件資料寫入至 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="823ce-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="823ce-103">此範例會使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="823ce-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="823ce-104">範例</span><span class="sxs-lookup"><span data-stu-id="823ce-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="823ce-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="823ce-105">Compiling the Code</span></span>  
 <span data-ttu-id="823ce-106">此類別必須有不具參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="823ce-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="823ce-107">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="823ce-107">Robust Programming</span></span>  
 <span data-ttu-id="823ce-108">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="823ce-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="823ce-109">正在序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="823ce-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="823ce-110">該檔案存在且為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="823ce-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="823ce-111">路徑太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="823ce-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="823ce-112">磁碟已滿 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="823ce-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="823ce-113">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="823ce-113">.NET Framework Security</span></span>  
 <span data-ttu-id="823ce-114">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="823ce-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="823ce-115">如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="823ce-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="823ce-116">如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="823ce-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="823ce-117">若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="823ce-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="823ce-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="823ce-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="823ce-119">如何：讀取物件資料，從 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="823ce-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="823ce-120">序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="823ce-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
