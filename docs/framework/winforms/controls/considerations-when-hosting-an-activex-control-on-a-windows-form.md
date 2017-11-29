---
title: "在 Windows Form 上裝載 ActiveX 控制項的考慮因素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ec828ca0b2bd8231d0baca72bf97bef566f2651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="0772f-102">在 Windows Form 上裝載 ActiveX 控制項的考慮因素</span><span class="sxs-lookup"><span data-stu-id="0772f-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="0772f-103">雖然 Windows Forms 已進行最佳化來裝載 Windows Forms 控制項，但是您仍然可以使用 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="0772f-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="0772f-104">規劃使用 ActiveX 控制項的應用程式時，請注意下列考量：</span><span class="sxs-lookup"><span data-stu-id="0772f-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
-   <span data-ttu-id="0772f-105">**安全性** Common Language Runtime 已增強程式碼存取安全性。</span><span class="sxs-lookup"><span data-stu-id="0772f-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="0772f-106">具備 Windows Forms 的應用程式可以在完全信任的環境中執行而不發生問題，而在半受信任的環境中則可以存取大部分的功能。</span><span class="sxs-lookup"><span data-stu-id="0772f-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="0772f-107">Windows Forms 控制項可以裝載在瀏覽器中，而且不會很複雜。</span><span class="sxs-lookup"><span data-stu-id="0772f-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="0772f-108">不過，Windows Forms 上的 ActiveX 控制項無法利用這些安全性加強功能。</span><span class="sxs-lookup"><span data-stu-id="0772f-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="0772f-109">執行 ActiveX 控制項需要 unmanaged 程式碼權限，就會以設定<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="0772f-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0772f-110">如需安全性和 unmanaged 程式碼權限的詳細資訊，請參閱<xref:System.Security.Permissions.SecurityPermissionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0772f-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
-   <span data-ttu-id="0772f-111">新增至 Windows Forms 的**擁有權總成本** ActiveX 控制項會與該 Windows Forms 一起完整部署，這樣會大幅增加所建立檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="0772f-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="0772f-112">此外，在 Windows Forms 上使用 ActiveX 控制項需要寫入至登錄。</span><span class="sxs-lookup"><span data-stu-id="0772f-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="0772f-113">這與不需要這麼做的 Windows Forms 控制項比起來，更容易擴散到使用者的電腦。</span><span class="sxs-lookup"><span data-stu-id="0772f-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0772f-114">使用 ActiveX 控制項需要使用 COM Interop 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="0772f-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="0772f-115">如需詳細資訊，請參閱 [Visual Basic 和 C# 中的 COM 互通性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="0772f-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0772f-116">如果 ActiveX 控制項的成員名稱符合已定義的名稱[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，ActiveX 控制項匯入工具會使用成員名稱的首碼則**Ctl**當建立<xref:System.Windows.Forms.AxHost>衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="0772f-116">If the name of a member of the ActiveX control matches a name defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="0772f-117">例如，如果您的 ActiveX 控制項有一個名為 **Layout** 的成員，它在 AxHost 衍生類別中就會被重新命名為 **CtlLayout**，因為 **Layout** 事件是在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中定義的。</span><span class="sxs-lookup"><span data-stu-id="0772f-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0772f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0772f-118">See Also</span></span>  
 [<span data-ttu-id="0772f-119">操作說明：將 ActiveX 控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0772f-119">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="0772f-120">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="0772f-120">Code Access Security</span></span>](../../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="0772f-121">比較各種語言和程式庫的控制項與可以透過程式設計的物件</span><span class="sxs-lookup"><span data-stu-id="0772f-121">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="0772f-122">將控制項加入 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0772f-122">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="0772f-123">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="0772f-123">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
