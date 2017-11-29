---
title: "剪貼簿的格式無效"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="a325c-102">剪貼簿的格式無效</span><span class="sxs-lookup"><span data-stu-id="a325c-102">Clipboard format is not valid</span></span>
<span data-ttu-id="a325c-103">指定的剪貼簿格式與不相容所執行的方法。</span><span class="sxs-lookup"><span data-stu-id="a325c-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="a325c-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="a325c-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="a325c-105">使用剪貼簿`GetText`或`SetText`方法以外的剪貼簿格式`vbCFText`或`vbCFLink`。</span><span class="sxs-lookup"><span data-stu-id="a325c-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="a325c-106">使用剪貼簿`GetData`或`SetData`方法以外的剪貼簿格式`vbCFBitmap`， `vbCFDIB`，或`vbCFMetafile`。</span><span class="sxs-lookup"><span data-stu-id="a325c-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="a325c-107">使用`DataObject``GetData`方法或`SetData`與 Microsoft Windows 登錄格式 (HC000-& HFFFF)，保留範圍中的剪貼簿格式的方法時該剪貼簿格式尚未註冊使用 Microsoft Windows。</span><span class="sxs-lookup"><span data-stu-id="a325c-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a325c-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a325c-108">To correct this error</span></span>  
  
-   <span data-ttu-id="a325c-109">移除無效的格式，並指定為有效。</span><span class="sxs-lookup"><span data-stu-id="a325c-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a325c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a325c-110">See Also</span></span>  
 [<span data-ttu-id="a325c-111">剪貼簿：新增其他格式</span><span class="sxs-lookup"><span data-stu-id="a325c-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
