---
title: 建立來源 Office Open XML 檔 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: d01755442a9b64e0577ace4eb05c6818dac9a824
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965245"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="34b08-102">建立來源 Office Open XML 檔 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34b08-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="34b08-103">這個主題顯示如何建立此教學課程中其他範例所使用的 Office Open XML WordprocessingML 文件。</span><span class="sxs-lookup"><span data-stu-id="34b08-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="34b08-104">如果您按照這些指示進行，您的輸出將會符合每個範例中提供的輸出。</span><span class="sxs-lookup"><span data-stu-id="34b08-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="34b08-105">不過，本教學課程中的範例將會使用任何有效的 WordprocessingML 文件。</span><span class="sxs-lookup"><span data-stu-id="34b08-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="34b08-106">若要建立本教學課程使用的文件，您必須已經安裝 Microsoft Office 2007 或更新版本；或者，您必須安裝 Microsoft Office 2003 與適用於 Word、Excel 和 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件。</span><span class="sxs-lookup"><span data-stu-id="34b08-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="34b08-107">建立 WordprocessingML 文件</span><span class="sxs-lookup"><span data-stu-id="34b08-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="34b08-108">若要建立 WordprocessingML 文件</span><span class="sxs-lookup"><span data-stu-id="34b08-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="34b08-109">建立新的 Microsoft Word 文件。</span><span class="sxs-lookup"><span data-stu-id="34b08-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="34b08-110">將下列文字貼到新的文件中：</span><span class="sxs-lookup"><span data-stu-id="34b08-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. <span data-ttu-id="34b08-111">將第一行的格式設定為「標題 1」樣式。</span><span class="sxs-lookup"><span data-stu-id="34b08-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="34b08-112">選取包含 Visual Basic 程式碼的行。</span><span class="sxs-lookup"><span data-stu-id="34b08-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="34b08-113">第一行開頭為 `Imports` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="34b08-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="34b08-114">最後一行是「結束類別」。</span><span class="sxs-lookup"><span data-stu-id="34b08-114">The last line is "End Class".</span></span> <span data-ttu-id="34b08-115">利用 Courier 字型設定這幾行的格式。</span><span class="sxs-lookup"><span data-stu-id="34b08-115">Format the lines with the courier font.</span></span> <span data-ttu-id="34b08-116">以新樣式設定格式，然後將新樣式命名為 "Code"。</span><span class="sxs-lookup"><span data-stu-id="34b08-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="34b08-117">最後，選取包含輸出的整行，然後使用 `Code` 樣式設定其格式。</span><span class="sxs-lookup"><span data-stu-id="34b08-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="34b08-118">儲存文件，然後將其命名為 SampleDoc.docx。</span><span class="sxs-lookup"><span data-stu-id="34b08-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="34b08-119">如果您要使用 Microsoft Word 2003，在 [存檔類型] 下拉式清單中選取 [Word 2007 文件]。</span><span class="sxs-lookup"><span data-stu-id="34b08-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b08-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34b08-120">See also</span></span>

- [<span data-ttu-id="34b08-121">教學課程：操作 WordprocessingML 檔中的內容 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34b08-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
