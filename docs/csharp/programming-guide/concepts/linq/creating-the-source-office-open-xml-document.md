---
title: 建立來源 Office Open XML 文件 (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 024b6c80cdedf38fd2dcee77562c0105df7bd033
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690103"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="4ee5e-102">建立來源 Office Open XML 文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="4ee5e-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="4ee5e-103">這個主題顯示如何建立此教學課程中其他範例所使用的 Office Open XML WordprocessingML 文件。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="4ee5e-104">如果您按照這些指示進行，您的輸出將會符合每個範例中提供的輸出。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="4ee5e-105">不過，本教學課程中的範例將會使用任何有效的 WordprocessingML 文件。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="4ee5e-106">若要建立本教學課程使用的文件，您必須已經安裝 Microsoft Office 2007 或更新版本；或者，您必須安裝 Microsoft Office 2003 與適用於 Word、Excel 和 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="4ee5e-107">建立 WordprocessingML 文件</span><span class="sxs-lookup"><span data-stu-id="4ee5e-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="4ee5e-108">若要建立 WordprocessingML 文件</span><span class="sxs-lookup"><span data-stu-id="4ee5e-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="4ee5e-109">建立新的 Microsoft Word 文件。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="4ee5e-110">將下列文字貼到新的文件中：</span><span class="sxs-lookup"><span data-stu-id="4ee5e-110">Paste the following text into the new document:</span></span>

    ```
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

3. <span data-ttu-id="4ee5e-111">將第一行的格式設定為「標題 1」樣式。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="4ee5e-112">選取包含 C# 程式碼的行。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="4ee5e-113">第一行開頭為 `using` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="4ee5e-114">最後一行是最後一個右邊的大括號。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-114">The last line is the last closing brace.</span></span> <span data-ttu-id="4ee5e-115">利用 Courier 字型設定這幾行的格式。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-115">Format the lines with the courier font.</span></span> <span data-ttu-id="4ee5e-116">以新樣式設定格式，然後將新樣式命名為 "Code"。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="4ee5e-117">最後，選取包含輸出的整行，然後使用 `Code` 樣式設定其格式。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="4ee5e-118">儲存文件，然後將其命名為 SampleDoc.docx。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4ee5e-119">如果您要使用 Microsoft Word 2003，在 [存檔類型]  下拉式清單中選取 [Word 2007 文件]  。</span><span class="sxs-lookup"><span data-stu-id="4ee5e-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
