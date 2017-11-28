---
title: "存取應用程式表單 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b029ce984f9cef540087181a83070b0c8aa8132
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="f40bf-102">存取應用程式表單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f40bf-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="f40bf-103">`My.Forms` 物件提供簡單的方法，讓您存取應用程式專案中宣告之每個 Windows Form 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f40bf-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="f40bf-104">您也可以使用 `My.Application` 物件的屬性來存取應用程式的啟動顯示畫面和主表單，並取得應用程式的開啟表單清單。</span><span class="sxs-lookup"><span data-stu-id="f40bf-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="f40bf-105">工作</span><span class="sxs-lookup"><span data-stu-id="f40bf-105">Tasks</span></span>  
 <span data-ttu-id="f40bf-106">下表列出用來示範如何存取應用程式表單的範例。</span><span class="sxs-lookup"><span data-stu-id="f40bf-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="f40bf-107">以</span><span class="sxs-lookup"><span data-stu-id="f40bf-107">To</span></span>|<span data-ttu-id="f40bf-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="f40bf-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="f40bf-109">從應用程式的表單存取另一個表單。</span><span class="sxs-lookup"><span data-stu-id="f40bf-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="f40bf-110">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="f40bf-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="f40bf-111">顯示應用程式所有開啟表單的標題。</span><span class="sxs-lookup"><span data-stu-id="f40bf-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="f40bf-112">當應用程式啟動時，使用狀態資訊更新啟動顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="f40bf-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="f40bf-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f40bf-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>  
 [<span data-ttu-id="f40bf-114">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="f40bf-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
