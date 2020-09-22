---
title: 剪貼簿的格式無效
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874587"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="5d89a-102">剪貼簿的格式無效</span><span class="sxs-lookup"><span data-stu-id="5d89a-102">Clipboard format is not valid</span></span>

<span data-ttu-id="5d89a-103">指定的剪貼簿格式與所執行的方法不相容。</span><span class="sxs-lookup"><span data-stu-id="5d89a-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="5d89a-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="5d89a-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="5d89a-105">使用剪貼簿 `GetText` 或方法搭配或以外的 `SetText` 剪貼簿格式 `vbCFText` `vbCFLink` 。</span><span class="sxs-lookup"><span data-stu-id="5d89a-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="5d89a-106">使用剪貼簿的 `GetData` 或 `SetData` 方法搭配、或以外的剪貼簿格式 `vbCFBitmap` `vbCFDIB` `vbCFMetafile` 。</span><span class="sxs-lookup"><span data-stu-id="5d89a-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="5d89a-107">使用的 `GetData` 或 `SetData` 方法，會 `DataObject` 在 microsoft windows 保留的範圍中，將剪貼簿格式用於已註冊的格式 ( # B0 HC000-&HFFFF) ，則表示該剪貼簿格式尚未向 microsoft windows 註冊。</span><span class="sxs-lookup"><span data-stu-id="5d89a-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d89a-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5d89a-108">To correct this error</span></span>  
  
- <span data-ttu-id="5d89a-109">請移除不正確格式，並指定一個有效的格式。</span><span class="sxs-lookup"><span data-stu-id="5d89a-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d89a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d89a-110">See also</span></span>

- [<span data-ttu-id="5d89a-111">剪貼簿：加入其他格式</span><span class="sxs-lookup"><span data-stu-id="5d89a-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
