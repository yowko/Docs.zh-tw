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
ms.openlocfilehash: 25ce3fdd98560aba0918431bb77d6f3f23a04784
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722460"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="71b3b-102">GDI+ 中的中繼檔</span><span class="sxs-lookup"><span data-stu-id="71b3b-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="71b3b-103">提供<xref:System.Drawing.Imaging.Metafile>類別，使您可以記錄並顯示中繼檔。</span><span class="sxs-lookup"><span data-stu-id="71b3b-103">provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="71b3b-104">中繼檔，也稱為向量映像中，是儲存為一連串的繪圖命令和設定的映像。</span><span class="sxs-lookup"><span data-stu-id="71b3b-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="71b3b-105">命令和設定記錄在<xref:System.Drawing.Imaging.Metafile>可以儲存在記憶體中或儲存至檔案或資料流物件。</span><span class="sxs-lookup"><span data-stu-id="71b3b-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="71b3b-106">中繼檔格式</span><span class="sxs-lookup"><span data-stu-id="71b3b-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="71b3b-107">可以顯示已儲存在下列格式的中繼檔：</span><span class="sxs-lookup"><span data-stu-id="71b3b-107">can display metafiles that have been stored in the following formats:</span></span>  
  
-   <span data-ttu-id="71b3b-108">Windows Metafile (WMF)</span><span class="sxs-lookup"><span data-stu-id="71b3b-108">Windows Metafile (WMF)</span></span>  
  
-   <span data-ttu-id="71b3b-109">加強型中繼檔 (EMF) </span><span class="sxs-lookup"><span data-stu-id="71b3b-109">Enhanced Metafile (EMF)</span></span>  
  
-   <span data-ttu-id="71b3b-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="71b3b-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="71b3b-111">EMF 和 EMF + 格式中，但不是在 WMF 格式時，就可以記錄的中繼檔。</span><span class="sxs-lookup"><span data-stu-id="71b3b-111">can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="71b3b-112">EMF + 是擴充功能，可讓 EMF[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]儲存的記錄。</span><span class="sxs-lookup"><span data-stu-id="71b3b-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="71b3b-113">有兩種變化 EMF + 格式：EMF + 只和 EMF + Dual。</span><span class="sxs-lookup"><span data-stu-id="71b3b-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="71b3b-114">EMF + 僅中繼檔只包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]記錄。</span><span class="sxs-lookup"><span data-stu-id="71b3b-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="71b3b-115">這類中繼檔可以藉由顯示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]但不是[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71b3b-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="71b3b-116">EMF + Dual 中繼檔包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]記錄。</span><span class="sxs-lookup"><span data-stu-id="71b3b-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="71b3b-117">每個[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]EMF + Dual 記錄中繼檔搭配替代[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]記錄。</span><span class="sxs-lookup"><span data-stu-id="71b3b-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="71b3b-118">這類中繼檔可以藉由顯示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]或由[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71b3b-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="71b3b-119">下列範例會顯示先前為檔案儲存在中繼檔。</span><span class="sxs-lookup"><span data-stu-id="71b3b-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="71b3b-120">在其左上角會顯示中繼檔 （100，100）。</span><span class="sxs-lookup"><span data-stu-id="71b3b-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="71b3b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71b3b-121">See also</span></span>
- [<span data-ttu-id="71b3b-122">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="71b3b-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
