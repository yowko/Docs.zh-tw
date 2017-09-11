---
title: "如何︰ 將物件資料寫入至 XML 檔案 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 27131f357c1f5afc75645bff88ae5d7cd2395617
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="0393f-102">如何︰ 將物件資料寫入至 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0393f-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="0393f-103">除非範例類別將物件寫入 XML 檔案中使用<xref:System.Xml.Serialization.XmlSerializer>類別。</xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="0393f-103">TThis example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0393f-104">範例</span><span class="sxs-lookup"><span data-stu-id="0393f-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0393f-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0393f-105">Compiling the Code</span></span>  
 <span data-ttu-id="0393f-106">這個類別必須具有不含參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="0393f-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0393f-107">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0393f-107">Robust Programming</span></span>  
 <span data-ttu-id="0393f-108">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="0393f-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="0393f-109">序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="0393f-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="0393f-110">該檔案存在，而且是唯讀的 (<xref:System.IO.IOException>)。</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="0393f-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="0393f-111">路徑過長 (<xref:System.IO.PathTooLongException>)。</xref:System.IO.PathTooLongException></span><span class="sxs-lookup"><span data-stu-id="0393f-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="0393f-112">磁碟已滿 (<xref:System.IO.IOException>)。</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="0393f-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0393f-113">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="0393f-113">.NET Framework Security</span></span>  
 <span data-ttu-id="0393f-114">如果檔案已經存在，這個範例會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="0393f-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="0393f-115">如果必須建立檔案的應用程式，該應用程式需要`Create`資料夾的存取。</span><span class="sxs-lookup"><span data-stu-id="0393f-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="0393f-116">如果檔案已經存在，應用程式只需要`Write`存取，較低權限。</span><span class="sxs-lookup"><span data-stu-id="0393f-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="0393f-117">如果可行的話，會在部署期間，建立檔案，並僅授與更安全`Read`存取單一檔案，而非`Create`資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="0393f-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0393f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0393f-118">See Also</span></span>  
 <span data-ttu-id="0393f-119"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="0393f-119"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="0393f-120"> [如何︰ 讀取 XML 檔案 (Visual Basic) 的物件資料](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="0393f-120"> [How to: Read Object Data from an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span></span>  
<span data-ttu-id="0393f-121"> [序列化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span><span class="sxs-lookup"><span data-stu-id="0393f-121"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span></span>
