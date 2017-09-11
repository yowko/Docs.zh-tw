---
title: "如何︰ 讀取 XML 檔案 (Visual Basic) 的物件資料 |Microsoft 文件"
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
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
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
ms.openlocfilehash: 3b9697f763a2d781c37960d46cbc7fa4536c84b4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="03c40-102">如何︰ 讀取 XML 檔案 (Visual Basic) 的物件資料</span><span class="sxs-lookup"><span data-stu-id="03c40-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="03c40-103">這個範例會讀取物件資料的先前寫入 XML 檔案中使用<xref:System.Xml.Serialization.XmlSerializer>類別。</xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="03c40-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03c40-104">範例</span><span class="sxs-lookup"><span data-stu-id="03c40-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03c40-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="03c40-105">Compiling the Code</span></span>  
 <span data-ttu-id="03c40-106">包含序列化的資料的檔案名稱來取代檔案名稱"c:\temp\SerializationOverview.xml"。</span><span class="sxs-lookup"><span data-stu-id="03c40-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="03c40-107">如需序列化資料的詳細資訊，請參閱[How to︰ 將物件資料寫入至 XML 檔案 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="03c40-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="03c40-108">這個類別必須具有不含參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="03c40-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="03c40-109">只有公用屬性和欄位會還原序列化。</span><span class="sxs-lookup"><span data-stu-id="03c40-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="03c40-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="03c40-110">Robust Programming</span></span>  
 <span data-ttu-id="03c40-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="03c40-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="03c40-112">序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="03c40-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="03c40-113">檔案中的資料不代表類別，以還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="03c40-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="03c40-114">檔案不存在 (<xref:System.IO.IOException>)。</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="03c40-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="03c40-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="03c40-115">.NET Framework Security</span></span>  
 <span data-ttu-id="03c40-116">永遠會先驗證輸入，並永遠不會還原序列化來自不受信任來源的資料。</span><span class="sxs-lookup"><span data-stu-id="03c40-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="03c40-117">重新建立的物件會還原序列化它的程式碼的權限的本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="03c40-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="03c40-118">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="03c40-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c40-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03c40-119">See Also</span></span>  
 <span data-ttu-id="03c40-120"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="03c40-120"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="03c40-121"> [如何︰ 將物件資料寫入至 XML 檔案 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="03c40-121"> [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span></span>  
<span data-ttu-id="03c40-122"> [序列化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="03c40-122"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span></span>  
<span data-ttu-id="03c40-123"> [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="03c40-123"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md)</span></span>
