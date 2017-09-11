---
title: "存取應用程式表單 (Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- forms, communicating between
- application forms, accessing
- forms, accessing one from another
- My.Forms object
- forms, accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 37c8aa78d945a4d13ce00239d6b0707977f2571e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="cc114-102">存取應用程式表單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc114-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="cc114-103">`My.Forms` 物件提供簡單的方法，讓您存取應用程式專案中宣告之每個 Windows Form 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cc114-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="cc114-104">您也可以使用 `My.Application` 物件的屬性來存取應用程式的啟動顯示畫面和主表單，並取得應用程式的開啟表單清單。</span><span class="sxs-lookup"><span data-stu-id="cc114-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="cc114-105">工作</span><span class="sxs-lookup"><span data-stu-id="cc114-105">Tasks</span></span>  
 <span data-ttu-id="cc114-106">下表列出用來示範如何存取應用程式表單的範例。</span><span class="sxs-lookup"><span data-stu-id="cc114-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="cc114-107">以</span><span class="sxs-lookup"><span data-stu-id="cc114-107">To</span></span>|<span data-ttu-id="cc114-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc114-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="cc114-109">從應用程式的表單存取另一個表單。</span><span class="sxs-lookup"><span data-stu-id="cc114-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="cc114-110">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="cc114-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="cc114-111">顯示應用程式所有開啟表單的標題。</span><span class="sxs-lookup"><span data-stu-id="cc114-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="cc114-112">當應用程式啟動時，使用狀態資訊更新啟動顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="cc114-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="cc114-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc114-113">See Also</span></span>  
 <span data-ttu-id="cc114-114"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></span><span class="sxs-lookup"><span data-stu-id="cc114-114"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></span></span>   
 <span data-ttu-id="cc114-115"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A></span><span class="sxs-lookup"><span data-stu-id="cc114-115"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A></span></span>   
 [<span data-ttu-id="cc114-116">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="cc114-116">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)

