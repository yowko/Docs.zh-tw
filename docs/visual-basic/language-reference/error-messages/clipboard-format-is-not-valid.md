---
title: 剪貼簿的格式無效
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649864"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="dcbf5-102">剪貼簿的格式無效</span><span class="sxs-lookup"><span data-stu-id="dcbf5-102">Clipboard format is not valid</span></span>
<span data-ttu-id="dcbf5-103">指定的剪貼簿格式與不相容所執行的方法。</span><span class="sxs-lookup"><span data-stu-id="dcbf5-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="dcbf5-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="dcbf5-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="dcbf5-105">使用剪貼簿`GetText`或是`SetText`方法以外的剪貼簿格式`vbCFText`或`vbCFLink`。</span><span class="sxs-lookup"><span data-stu-id="dcbf5-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="dcbf5-106">使用剪貼簿`GetData`或是`SetData`方法以外的剪貼簿格式`vbCFBitmap`， `vbCFDIB`，或`vbCFMetafile`。</span><span class="sxs-lookup"><span data-stu-id="dcbf5-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="dcbf5-107">使用`GetData`或是`SetData`方法`DataObject`與 Microsoft Windows 登錄格式 （HC000-& HFFFF），保留範圍的剪貼簿格式時該剪貼簿格式尚未註冊使用 Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="dcbf5-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dcbf5-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="dcbf5-108">To correct this error</span></span>  
  
- <span data-ttu-id="dcbf5-109">移除無效的格式，並指定一個有效的帳戶。</span><span class="sxs-lookup"><span data-stu-id="dcbf5-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbf5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcbf5-110">See also</span></span>

- [<span data-ttu-id="dcbf5-111">剪貼簿：加入其他格式</span><span class="sxs-lookup"><span data-stu-id="dcbf5-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
