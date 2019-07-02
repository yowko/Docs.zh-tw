---
title: GDI+ 中的中繼檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504581"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="6235c-102">GDI+ 中的中繼檔</span><span class="sxs-lookup"><span data-stu-id="6235c-102">Metafiles in GDI+</span></span>
<span data-ttu-id="6235c-103">GDI + 提供<xref:System.Drawing.Imaging.Metafile>類別，使您可以記錄並顯示中繼檔。</span><span class="sxs-lookup"><span data-stu-id="6235c-103">GDI+ provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="6235c-104">中繼檔，也稱為向量映像中，是儲存為一連串的繪圖命令和設定的映像。</span><span class="sxs-lookup"><span data-stu-id="6235c-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="6235c-105">命令和設定記錄在<xref:System.Drawing.Imaging.Metafile>可以儲存在記憶體中或儲存至檔案或資料流物件。</span><span class="sxs-lookup"><span data-stu-id="6235c-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="6235c-106">中繼檔格式</span><span class="sxs-lookup"><span data-stu-id="6235c-106">Metafile Formats</span></span>  
 <span data-ttu-id="6235c-107">GDI + 可以顯示已儲存在下列格式的中繼檔：</span><span class="sxs-lookup"><span data-stu-id="6235c-107">GDI+ can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="6235c-108">Windows Metafile (WMF)</span><span class="sxs-lookup"><span data-stu-id="6235c-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="6235c-109">加強型中繼檔 (EMF)</span><span class="sxs-lookup"><span data-stu-id="6235c-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="6235c-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="6235c-110">EMF+</span></span>  
  
 <span data-ttu-id="6235c-111">GDI + 可以記錄的中繼檔的 EMF 和 EMF + 格式，但不是在 WMF 格式。</span><span class="sxs-lookup"><span data-stu-id="6235c-111">GDI+ can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="6235c-112">EMF + 是允許 GDI + 記錄来儲存的 EMF 的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="6235c-112">EMF+ is an extension to EMF that allows GDI+ records to be stored.</span></span> <span data-ttu-id="6235c-113">有兩種變化 EMF + 格式：EMF + 只和 EMF + Dual。</span><span class="sxs-lookup"><span data-stu-id="6235c-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="6235c-114">EMF + 僅中繼檔僅包含 GDI + 記錄。</span><span class="sxs-lookup"><span data-stu-id="6235c-114">EMF+ Only metafiles contain only GDI+ records.</span></span> <span data-ttu-id="6235c-115">這類中繼檔可以在 GDI + 中，但不是由 GDI 顯示。</span><span class="sxs-lookup"><span data-stu-id="6235c-115">Such metafiles can be displayed by GDI+ but not by GDI.</span></span> <span data-ttu-id="6235c-116">EMF + Dual 中繼檔含有 GDI + 和 GDI 記錄。</span><span class="sxs-lookup"><span data-stu-id="6235c-116">EMF+ Dual metafiles contain GDI+ and GDI records.</span></span> <span data-ttu-id="6235c-117">EMF + Dual 中繼檔中的每個 GDI + 記錄會與替代的 GDI 記錄配對。</span><span class="sxs-lookup"><span data-stu-id="6235c-117">Each GDI+ record in an EMF+ Dual metafile is paired with an alternate GDI record.</span></span> <span data-ttu-id="6235c-118">GDI 或 GDI + 時，會顯示這類中繼檔。</span><span class="sxs-lookup"><span data-stu-id="6235c-118">Such metafiles can be displayed by GDI+ or by GDI.</span></span>  
  
 <span data-ttu-id="6235c-119">下列範例會顯示先前為檔案儲存在中繼檔。</span><span class="sxs-lookup"><span data-stu-id="6235c-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="6235c-120">在其左上角會顯示中繼檔 （100，100）。</span><span class="sxs-lookup"><span data-stu-id="6235c-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="6235c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6235c-121">See also</span></span>

- [<span data-ttu-id="6235c-122">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="6235c-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
