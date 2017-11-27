---
title: "不允許使用 Set"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID387
ms.assetid: 809f6768-7dd7-4632-b4dd-83856edfdb48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 854384a84ccc6f31aef6c350049cc18c8a72a6fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="set-not-permitted"></a><span data-ttu-id="c92b4-102">不允許使用 Set</span><span class="sxs-lookup"><span data-stu-id="c92b4-102">Set not permitted</span></span>
<span data-ttu-id="c92b4-103">您嘗試要變更無法在執行階段設定其設定的屬性，或是只能在某些情況下設定其設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="c92b4-103">You attempted to change a property whose settings either cannot be set at run time or else can only be set under certain conditions.</span></span> <span data-ttu-id="c92b4-104">例如，您可能嘗試在執行階段變更表單的 `Appearance`、 `ControlBox`、`MinButton`或 `MaxButton` 屬性設定，或是您可能嘗試針對父功能表上最後一個剩餘可見的子功能表，將 `Visible` 屬性設為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="c92b4-104">For example, you may have tried to change the `Appearance`, `ControlBox`,`MinButton`, or `MaxButton` property settings for the form at run time, or you may have tried to set the `Visible` property to `False` for the last remaining visible submenu on a parent menu.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c92b4-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c92b4-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c92b4-106">請檢查屬性，並判斷在哪些情況下可以設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c92b4-106">Check the property and determine under what conditions it can be set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92b4-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c92b4-107">See Also</span></span>  
 [<span data-ttu-id="c92b4-108">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="c92b4-108">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
