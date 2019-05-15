---
title: 在 Windows Form 上裝載 ActiveX 控制項的考慮因素
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 4b604502e0fea591460f30cae28b64ff1703da65
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589429"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="899ad-102">在 Windows Form 上裝載 ActiveX 控制項的考慮因素</span><span class="sxs-lookup"><span data-stu-id="899ad-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="899ad-103">雖然 Windows Forms 已進行最佳化來裝載 Windows Forms 控制項，但是您仍然可以使用 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="899ad-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="899ad-104">規劃使用 ActiveX 控制項的應用程式時，請注意下列考量：</span><span class="sxs-lookup"><span data-stu-id="899ad-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
- <span data-ttu-id="899ad-105">**安全性** Common Language Runtime 已增強程式碼存取安全性。</span><span class="sxs-lookup"><span data-stu-id="899ad-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="899ad-106">具備 Windows Forms 的應用程式可以在完全信任的環境中執行而不發生問題，而在半受信任的環境中則可以存取大部分的功能。</span><span class="sxs-lookup"><span data-stu-id="899ad-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="899ad-107">Windows Forms 控制項可以裝載在瀏覽器中，而且不會很複雜。</span><span class="sxs-lookup"><span data-stu-id="899ad-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="899ad-108">不過，Windows Forms 上的 ActiveX 控制項無法利用這些安全性加強功能。</span><span class="sxs-lookup"><span data-stu-id="899ad-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="899ad-109">執行 ActiveX 控制項需要 unmanaged 程式碼權限，這會使用設定<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="899ad-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="899ad-110">如需有關安全性和 unmanaged 程式碼權限的詳細資訊，請參閱<xref:System.Security.Permissions.SecurityPermissionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="899ad-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
- <span data-ttu-id="899ad-111">新增至 Windows Forms 的**擁有權總成本** ActiveX 控制項會與該 Windows Forms 一起完整部署，這樣會大幅增加所建立檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="899ad-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="899ad-112">此外，在 Windows Forms 上使用 ActiveX 控制項需要寫入至登錄。</span><span class="sxs-lookup"><span data-stu-id="899ad-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="899ad-113">這與不需要這麼做的 Windows Forms 控制項比起來，更容易擴散到使用者的電腦。</span><span class="sxs-lookup"><span data-stu-id="899ad-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="899ad-114">使用 ActiveX 控制項需要使用 COM Interop 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="899ad-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="899ad-115">如需詳細資訊，請參閱 [Visual Basic 和 C# 中的 COM 互通性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="899ad-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="899ad-116">如果 ActiveX 控制項的成員名稱符合.NET Framework 中定義的名稱，則 ActiveX 控制項匯入工具會在成員名稱前面加**Ctl**當它建立<xref:System.Windows.Forms.AxHost>衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="899ad-116">If the name of a member of the ActiveX control matches a name defined in the .NET Framework, then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="899ad-117">比方說，如果您的 ActiveX 控制項具有名為的成員**版面配置**，它會重新命名**CtlLayout** AxHost 衍生類別中因為**版面配置**內定義事件。NET Framework。</span><span class="sxs-lookup"><span data-stu-id="899ad-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899ad-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="899ad-118">See also</span></span>

- [<span data-ttu-id="899ad-119">如何：將 ActiveX 控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="899ad-119">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="899ad-120">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="899ad-120">Code Access Security</span></span>](../../misc/code-access-security.md)
- <span data-ttu-id="899ad-121">[比較各種語言和程式庫的控制項與可以透過程式設計的物件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="899ad-121">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="899ad-122">將控制項加入 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="899ad-122">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="899ad-123">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="899ad-123">Windows Forms Controls</span></span>](index.md)
