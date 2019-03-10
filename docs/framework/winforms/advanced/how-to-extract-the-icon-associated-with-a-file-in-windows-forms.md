---
title: HOW TO：擷取與 Windows Form 中檔案相關聯的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 5cbce48643d21418d580a6db44f86b00cf50fb9d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714186"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="bc0ea-102">HOW TO：擷取與 Windows Form 中檔案相關聯的圖示</span><span class="sxs-lookup"><span data-stu-id="bc0ea-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="bc0ea-103">許多檔案有內嵌提供相關聯的檔案類型的視覺表示法的圖示。</span><span class="sxs-lookup"><span data-stu-id="bc0ea-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="bc0ea-104">比方說，Microsoft Word 文件會包含其識別為 Word 文件的圖示。</span><span class="sxs-lookup"><span data-stu-id="bc0ea-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="bc0ea-105">當清單控制項或資料表控制項中顯示的檔案，您可能想要顯示代表每個檔案名稱旁邊的檔案類型的圖示。</span><span class="sxs-lookup"><span data-stu-id="bc0ea-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="bc0ea-106">您可以輕鬆地使用<xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="bc0ea-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc0ea-107">範例</span><span class="sxs-lookup"><span data-stu-id="bc0ea-107">Example</span></span>  
 <span data-ttu-id="bc0ea-108">下列程式碼範例示範如何擷取與檔案相關聯的圖示，並顯示檔案名稱和其相關聯的圖示中<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="bc0ea-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc0ea-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bc0ea-109">Compiling the Code</span></span>  
 <span data-ttu-id="bc0ea-110">若要編譯範例：</span><span class="sxs-lookup"><span data-stu-id="bc0ea-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="bc0ea-111">將上述程式碼貼到 Windows Form，並呼叫`ExtractAssociatedIconExample`從表單的建構函式的方法或<xref:System.Windows.Forms.Form.Load>事件處理方法。</span><span class="sxs-lookup"><span data-stu-id="bc0ea-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="bc0ea-112">您必須先確定您的表單匯入<xref:System.IO>命名空間。</span><span class="sxs-lookup"><span data-stu-id="bc0ea-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0ea-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc0ea-113">See also</span></span>
- [<span data-ttu-id="bc0ea-114">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="bc0ea-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="bc0ea-115">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="bc0ea-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
