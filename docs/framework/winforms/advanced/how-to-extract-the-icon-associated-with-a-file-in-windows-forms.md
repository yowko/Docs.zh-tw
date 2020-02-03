---
title: 如何：解壓縮與檔案相關聯的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742537"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="e4e9f-102">如何：擷取與 Windows Form 中檔案相關的圖示</span><span class="sxs-lookup"><span data-stu-id="e4e9f-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="e4e9f-103">許多檔案都有內嵌的圖示，可提供相關聯檔案類型的視覺標記法。</span><span class="sxs-lookup"><span data-stu-id="e4e9f-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="e4e9f-104">例如，Microsoft Word 檔包含將其識別為 Word 檔的圖示。</span><span class="sxs-lookup"><span data-stu-id="e4e9f-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="e4e9f-105">在清單控制項或表格控制項中顯示檔案時，您可能會想要顯示代表每個檔案名旁邊之檔案類型的圖示。</span><span class="sxs-lookup"><span data-stu-id="e4e9f-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="e4e9f-106">您可以使用 <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> 方法輕鬆地執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="e4e9f-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4e9f-107">範例</span><span class="sxs-lookup"><span data-stu-id="e4e9f-107">Example</span></span>  
 <span data-ttu-id="e4e9f-108">下列程式碼範例示範如何將與檔案相關聯的圖示解壓縮，並在 <xref:System.Windows.Forms.ListView> 控制項中顯示檔案名和其相關聯的圖示。</span><span class="sxs-lookup"><span data-stu-id="e4e9f-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4e9f-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e4e9f-109">Compiling the Code</span></span>  
 <span data-ttu-id="e4e9f-110">若要編譯範例：</span><span class="sxs-lookup"><span data-stu-id="e4e9f-110">To compile the example:</span></span>  
  
- <span data-ttu-id="e4e9f-111">將上述程式碼貼入 Windows Form，並從表單的函式或 <xref:System.Windows.Forms.Form.Load> 事件處理方法呼叫 `ExtractAssociatedIconExample` 方法。</span><span class="sxs-lookup"><span data-stu-id="e4e9f-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="e4e9f-112">您必須確定表單會匯入 <xref:System.IO> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4e9f-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e9f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4e9f-113">See also</span></span>

- [<span data-ttu-id="e4e9f-114">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="e4e9f-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="e4e9f-115">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="e4e9f-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
