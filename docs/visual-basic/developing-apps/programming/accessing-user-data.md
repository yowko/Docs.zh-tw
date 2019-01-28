---
title: 存取使用者資料 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- domain names [Visual Basic], retrieving
- data [Visual Basic], accessing user data
- My.User object [Visual Basic], tasks
- user data [Visual Basic], domain
- user names [Visual Basic], retrieving
- user data [Visual Basic], accessing
- login names [Visual Basic]
- examples [Visual Basic], accessing user data
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
ms.openlocfilehash: 5ff071aadb189cec839b9cb41d510764a9187363
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605485"
---
# <a name="accessing-user-data-visual-basic"></a><span data-ttu-id="4c742-102">存取使用者資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c742-102">Accessing User Data (Visual Basic)</span></span>
<span data-ttu-id="4c742-103">本節包含處理 `My.User` 物件以及可使用它完成的工作等主題。</span><span class="sxs-lookup"><span data-stu-id="4c742-103">This section contains topics dealing with the `My.User` object and tasks that you can accomplish with it.</span></span>  
  
 <span data-ttu-id="4c742-104">`My.User` 物件透過傳回實作 <xref:System.Security.Principal.IPrincipal> 介面的物件，讓您存取已登入使用者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4c742-104">The `My.User` object provides access to information about the logged-on user by returning an object that implements the <xref:System.Security.Principal.IPrincipal> interface.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="4c742-105">工作</span><span class="sxs-lookup"><span data-stu-id="4c742-105">Tasks</span></span>  
  
|<span data-ttu-id="4c742-106">以</span><span class="sxs-lookup"><span data-stu-id="4c742-106">To</span></span>|<span data-ttu-id="4c742-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c742-107">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="4c742-108">取得使用者的登入名稱</span><span class="sxs-lookup"><span data-stu-id="4c742-108">Get the user's login name</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|<span data-ttu-id="4c742-109">如果應用程式使用 Windows 驗證即可取得使用者的網域名稱</span><span class="sxs-lookup"><span data-stu-id="4c742-109">Get the user's domain name, if the application uses Windows authentication</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|<span data-ttu-id="4c742-110">判斷使用者的角色</span><span class="sxs-lookup"><span data-stu-id="4c742-110">Determine the user's role</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="4c742-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c742-111">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
