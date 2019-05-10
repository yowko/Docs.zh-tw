---
title: HOW TO：讀取物件資料，從 XML 檔案 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: b1e9033d7aba8b4f423f29cd4fb4f7efbbe17a29
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624380"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="1e9cd-102">HOW TO：讀取物件資料，從 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e9cd-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="1e9cd-103">此範例會讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e9cd-104">範例</span><span class="sxs-lookup"><span data-stu-id="1e9cd-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e9cd-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1e9cd-105">Compiling the Code</span></span>  
 <span data-ttu-id="1e9cd-106">以內含序列化資料之檔案的名稱取代檔案名稱 "c:\temp\SerializationOverview.xml"。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="1e9cd-107">如需將資料序列化的詳細資訊，請參閱[如何：將物件資料寫入至 XML 檔案 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="1e9cd-108">此類別必須有不具參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="1e9cd-109">只會還原序列化公用屬性和欄位。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1e9cd-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1e9cd-110">Robust Programming</span></span>  
 <span data-ttu-id="1e9cd-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="1e9cd-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1e9cd-112">正在序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="1e9cd-113">檔案中的資料不是來自要還原序列化之類別的資料。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="1e9cd-114">檔案不存在 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1e9cd-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1e9cd-115">.NET Framework Security</span></span>  
 <span data-ttu-id="1e9cd-116">永遠會驗證輸入，而且絕不會還原序列化來自未受信任來源的資料。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="1e9cd-117">重新建立的物件會以還原序列化該物件之程式碼的權限，在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="1e9cd-118">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="1e9cd-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9cd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9cd-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="1e9cd-120">如何：將物件資料寫入至 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e9cd-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="1e9cd-121">序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e9cd-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="1e9cd-122">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="1e9cd-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
