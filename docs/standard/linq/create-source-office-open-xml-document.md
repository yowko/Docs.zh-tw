---
title: 建立來源 Office Open XML 檔-LINQ to XML
description: 瞭解如何建立本教學課程中其他範例所使用的 Office Open XML WordprocessingML 檔。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: b3401d7309879661dcfc7062418ee75430dccf35
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552083"
---
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a><span data-ttu-id="ec6b0-103">建立來源 Office Open XML 檔 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="ec6b0-103">Create the source Office Open XML document (LINQ to XML)</span></span>

<span data-ttu-id="ec6b0-104">本文說明如何建立本教學課程中其他範例所使用的 Office Open XML WordprocessingML 檔。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-104">This article shows how to create the Office Open XML WordprocessingML document used by the other examples in this tutorial.</span></span> <span data-ttu-id="ec6b0-105">如果您按照這些指示進行，您的輸出將會符合每個範例中提供的輸出。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-105">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="ec6b0-106">不過，本教學課程中的範例將會使用任何有效的 WordprocessingML 文件。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-106">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="ec6b0-107">若要建立本教學課程使用的文件，您必須已經安裝 Microsoft Office 2007 或更新版本；或者，您必須安裝 Microsoft Office 2003 與適用於 Word、Excel 和 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-107">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="create-the-wordprocessingml-document"></a><span data-ttu-id="ec6b0-108">建立 WordprocessingML 檔</span><span class="sxs-lookup"><span data-stu-id="ec6b0-108">Create the WordprocessingML document</span></span>

<span data-ttu-id="ec6b0-109">使用下列步驟來建立 WordprocessingML 檔：</span><span class="sxs-lookup"><span data-stu-id="ec6b0-109">Use the following steps to create the WordprocessingML document:</span></span>

1. <span data-ttu-id="ec6b0-110">建立新的 Microsoft Word 文件。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-110">Create a new Microsoft Word document.</span></span>
1. <span data-ttu-id="ec6b0-111">將下列文字貼到新的檔中。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-111">Paste the following text into the new document.</span></span>
   1. <span data-ttu-id="ec6b0-112">若為 c #，請使用下列文字：</span><span class="sxs-lookup"><span data-stu-id="ec6b0-112">For C#, use this text:</span></span>

         ```text
         Parsing WordprocessingML with LINQ to XML

         The following example prints to the console.

         using System;

            class Program {
               public static void Main(string[] args) {
               Console.WriteLine("Hello World");
            }
         }

         This example produces the following output:

         Hello World
         ```

   1. <span data-ttu-id="ec6b0-113">針對 Visual Basic，請使用下列文字：</span><span class="sxs-lookup"><span data-stu-id="ec6b0-113">For Visual Basic, use this text:</span></span>

      ```text
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

1. <span data-ttu-id="ec6b0-114">將第一行的格式設定為「標題 1」樣式。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-114">Format the first line with the style "Heading 1".</span></span>
1. <span data-ttu-id="ec6b0-115">若為 c #，請選取包含 c # 程式碼的程式列。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-115">For C#, select the lines that contain the C# code.</span></span> <span data-ttu-id="ec6b0-116">第一行開頭為 `using` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-116">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="ec6b0-117">最後一行是最後一個右邊的大括號。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-117">The last line is the last closing brace.</span></span> <span data-ttu-id="ec6b0-118">利用 Courier 字型設定這幾行的格式。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-118">Format the lines with the courier font.</span></span> <span data-ttu-id="ec6b0-119">以新樣式設定格式，然後將新樣式命名為 "Code"。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-119">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="ec6b0-120">針對 Visual Basic，請選取包含 Visual Basic 代碼的行。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-120">For Visual Basic, select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="ec6b0-121">第一行開頭為 `Imports` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-121">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="ec6b0-122">最後一行是「End Class」。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-122">The last line is "End Class".</span></span> <span data-ttu-id="ec6b0-123">利用 Courier 字型設定這幾行的格式。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-123">Format the lines with the courier font.</span></span> <span data-ttu-id="ec6b0-124">以新樣式設定格式，然後將新樣式命名為 "Code"。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-124">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="ec6b0-125">最後，選取包含輸出的整行，然後使用 `Code` 樣式設定其格式。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-125">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>
1. <span data-ttu-id="ec6b0-126">儲存文件，然後將其命名為 SampleDoc.docx。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-126">Save the document, and name it SampleDoc.docx.</span></span>

> [!NOTE]
> <span data-ttu-id="ec6b0-127">如果您使用的是 Microsoft Word 2003，請在 [檔**類型**] 下拉式清單中選取 [ **Word 2007 檔**]。</span><span class="sxs-lookup"><span data-stu-id="ec6b0-127">If you're using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec6b0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec6b0-128">See also</span></span>

- [<span data-ttu-id="ec6b0-129">教學課程：操作 WordprocessingML 檔中的內容</span><span class="sxs-lookup"><span data-stu-id="ec6b0-129">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
