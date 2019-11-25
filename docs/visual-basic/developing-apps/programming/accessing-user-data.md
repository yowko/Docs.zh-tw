---
title: 存取使用者資料
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
ms.openlocfilehash: 463d3bc77237482d4cd568b9558bb72cd19e7216
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349208"
---
# <a name="accessing-user-data-visual-basic"></a><span data-ttu-id="3bffc-102">存取使用者資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bffc-102">Accessing User Data (Visual Basic)</span></span>

<span data-ttu-id="3bffc-103">本節包含處理 `My.User` 物件以及可使用它完成的工作等主題。</span><span class="sxs-lookup"><span data-stu-id="3bffc-103">This section contains topics dealing with the `My.User` object and tasks that you can accomplish with it.</span></span>  
  
 <span data-ttu-id="3bffc-104">`My.User` 物件透過傳回實作 <xref:System.Security.Principal.IPrincipal> 介面的物件，讓您存取已登入使用者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3bffc-104">The `My.User` object provides access to information about the logged-on user by returning an object that implements the <xref:System.Security.Principal.IPrincipal> interface.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3bffc-105">工作</span><span class="sxs-lookup"><span data-stu-id="3bffc-105">Tasks</span></span>  
  
|<span data-ttu-id="3bffc-106">若要</span><span class="sxs-lookup"><span data-stu-id="3bffc-106">To</span></span>|<span data-ttu-id="3bffc-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="3bffc-107">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="3bffc-108">取得使用者的登入名稱</span><span class="sxs-lookup"><span data-stu-id="3bffc-108">Get the user's login name</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|<span data-ttu-id="3bffc-109">如果應用程式使用 Windows 驗證即可取得使用者的網域名稱</span><span class="sxs-lookup"><span data-stu-id="3bffc-109">Get the user's domain name, if the application uses Windows authentication</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|<span data-ttu-id="3bffc-110">判斷使用者的角色</span><span class="sxs-lookup"><span data-stu-id="3bffc-110">Determine the user's role</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="3bffc-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="3bffc-111">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.User>
