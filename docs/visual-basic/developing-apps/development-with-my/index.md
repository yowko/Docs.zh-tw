---
title: "使用 My 進行開發 (Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWpfExtension.Windows
dev_langs:
- VB
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
caps.latest.revision: 26
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
ms.openlocfilehash: 3dae5e12baeb82c238381fb9e144c434816dcfb4
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="468ba-102">使用 My 進行開發 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="468ba-102">Development with My (Visual Basic)</span></span>
<span data-ttu-id="468ba-103">Visual Basic 提供可進行快速應用程式開發的新功能來提高產能且易於使用，同時還能提供電源。</span><span class="sxs-lookup"><span data-stu-id="468ba-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="468ba-104">這其中一個功能稱為 `My`，可提供對與應用程式及其執行階段環境相關資訊和預設物件執行個體的存取。</span><span class="sxs-lookup"><span data-stu-id="468ba-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="468ba-105">此資訊的組織方式是以可透過 IntelliSense 進行探索且邏輯上根據使用方式分隔的格式來進行。</span><span class="sxs-lookup"><span data-stu-id="468ba-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="468ba-106">`My` 的最上層成員會公開為物件。</span><span class="sxs-lookup"><span data-stu-id="468ba-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="468ba-107">每個物件的運作方式類似具有 `Shared` 成員的命名空間或類別，而它會公開一組相關的成員。</span><span class="sxs-lookup"><span data-stu-id="468ba-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="468ba-108">此表格顯示最上層 `My` 物件及其彼此間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="468ba-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 <span data-ttu-id="468ba-109">![My 的物件模型](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span><span class="sxs-lookup"><span data-stu-id="468ba-109">![Object Model for My](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="468ba-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="468ba-110">In This Section</span></span>  
 [<span data-ttu-id="468ba-111">使用 My.Application、My.Computer 和 My.User 執行工作</span><span class="sxs-lookup"><span data-stu-id="468ba-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="468ba-112">描述三種中央 `My` 物件 (`My.Application`、`My.Computer` 和 `My.User`)，它們提供對資訊和功能的存取。</span><span class="sxs-lookup"><span data-stu-id="468ba-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="468ba-113">My.Forms 和 My.WebServices 提供的預設物件執行個體</span><span class="sxs-lookup"><span data-stu-id="468ba-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="468ba-114">描述 `My.Forms` 和 `My.WebServices` 物件，它們提供對您應用程式所使用的表單、資料來源和 XML Web 服務的存取。</span><span class="sxs-lookup"><span data-stu-id="468ba-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="468ba-115">使用 My.Resources 和 My.Settings 進行快速應用程式開發</span><span class="sxs-lookup"><span data-stu-id="468ba-115">Rapid Application Development with My.Resources and My.Settings</span></span>](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="468ba-116">描述 `My.Resources` 和 `My.Settings` 物件，它們提供對應用程式資源和設定的存取。</span><span class="sxs-lookup"><span data-stu-id="468ba-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="468ba-117">Visual Basic 應用程式模型概觀</span><span class="sxs-lookup"><span data-stu-id="468ba-117">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="468ba-118">描述 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 應用程式啟動/關機模型。</span><span class="sxs-lookup"><span data-stu-id="468ba-118">Describes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="468ba-119">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="468ba-119">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="468ba-120">提供有關 `My` 功能可在不同專案型別中使用的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="468ba-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="468ba-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="468ba-121">See Also</span></span>  
 <span data-ttu-id="468ba-122"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></span><span class="sxs-lookup"><span data-stu-id="468ba-122"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></span></span>   
 <span data-ttu-id="468ba-123"><xref:Microsoft.VisualBasic.Devices.Computer></span><span class="sxs-lookup"><span data-stu-id="468ba-123"><xref:Microsoft.VisualBasic.Devices.Computer></span></span>   
 <span data-ttu-id="468ba-124"><xref:Microsoft.VisualBasic.ApplicationServices.User></span><span class="sxs-lookup"><span data-stu-id="468ba-124"><xref:Microsoft.VisualBasic.ApplicationServices.User></span></span>   
 <span data-ttu-id="468ba-125">[My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md) </span><span class="sxs-lookup"><span data-stu-id="468ba-125">[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md) </span></span>  
 <span data-ttu-id="468ba-126">[My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md) </span><span class="sxs-lookup"><span data-stu-id="468ba-126">[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md) </span></span>  
 [<span data-ttu-id="468ba-127">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="468ba-127">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)

