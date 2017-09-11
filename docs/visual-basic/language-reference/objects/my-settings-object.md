---
title: "My.Settings 物件 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4d6ee6d2d54c0e3a4af3b7cdec5f81166ce3ddce
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="mysettings-object"></a><span data-ttu-id="407ba-102">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="407ba-102">My.Settings Object</span></span>
<span data-ttu-id="407ba-103">提供屬性和方法來存取應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="407ba-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="407ba-104">備註</span><span class="sxs-lookup"><span data-stu-id="407ba-104">Remarks</span></span>  
 <span data-ttu-id="407ba-105">`My.Settings`物件提供應用程式的設定存取權，並可讓您動態儲存和擷取屬性設定和應用程式的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="407ba-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="407ba-106">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="407ba-106">For more information, see [Managing Application Settings (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="407ba-107">屬性</span><span class="sxs-lookup"><span data-stu-id="407ba-107">Properties</span></span>  
 <span data-ttu-id="407ba-108">屬性的`My.Settings`物件提供存取您的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="407ba-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="407ba-109">若要新增或移除設定，使用**設定設計工具**。</span><span class="sxs-lookup"><span data-stu-id="407ba-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="407ba-110">每個設定**名稱**，**類型**，**範圍**，和**值**，以及這些設定會決定要存取的每個設定的屬性會出現在`My.Settings`物件︰</span><span class="sxs-lookup"><span data-stu-id="407ba-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="407ba-111">**名稱**判斷屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="407ba-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="407ba-112">**型別**判斷屬性的型別。</span><span class="sxs-lookup"><span data-stu-id="407ba-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="407ba-113">**範圍**指出屬性是否為唯讀。</span><span class="sxs-lookup"><span data-stu-id="407ba-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="407ba-114">如果值為**應用程式**，屬性是唯讀; 如果值為**使用者**，屬性是讀寫。</span><span class="sxs-lookup"><span data-stu-id="407ba-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="407ba-115">**值**是屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="407ba-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="407ba-116">方法</span><span class="sxs-lookup"><span data-stu-id="407ba-116">Methods</span></span>  
  
|<span data-ttu-id="407ba-117">方法</span><span class="sxs-lookup"><span data-stu-id="407ba-117">Method</span></span>|<span data-ttu-id="407ba-118">描述</span><span class="sxs-lookup"><span data-stu-id="407ba-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="407ba-119">重新載入使用者設定從上次儲存的值。</span><span class="sxs-lookup"><span data-stu-id="407ba-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="407ba-120">儲存目前的使用者設定。</span><span class="sxs-lookup"><span data-stu-id="407ba-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="407ba-121">`My.Settings`物件也會提供進階的屬性和方法，繼承自<xref:System.Configuration.ApplicationSettingsBase>類別。</xref:System.Configuration.ApplicationSettingsBase></span><span class="sxs-lookup"><span data-stu-id="407ba-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="407ba-122">工作</span><span class="sxs-lookup"><span data-stu-id="407ba-122">Tasks</span></span>  
 <span data-ttu-id="407ba-123">下表列出包含工作的範例`My.Settings`物件。</span><span class="sxs-lookup"><span data-stu-id="407ba-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="407ba-124">以</span><span class="sxs-lookup"><span data-stu-id="407ba-124">To</span></span>|<span data-ttu-id="407ba-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="407ba-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="407ba-126">讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="407ba-126">Read an application setting</span></span>|[<span data-ttu-id="407ba-127">如何︰ 讀取 Visual Basic 中的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="407ba-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="407ba-128">變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="407ba-128">Change a user setting</span></span>|[<span data-ttu-id="407ba-129">如何︰ 變更 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="407ba-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="407ba-130">保存使用者設定</span><span class="sxs-lookup"><span data-stu-id="407ba-130">Persist user settings</span></span>|[<span data-ttu-id="407ba-131">如何︰ 保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="407ba-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="407ba-132">建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="407ba-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="407ba-133">如何︰ 建立 Visual Basic 中的使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="407ba-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="407ba-134">範例</span><span class="sxs-lookup"><span data-stu-id="407ba-134">Example</span></span>  
 <span data-ttu-id="407ba-135">此範例中顯示的值`Nickname`設定。</span><span class="sxs-lookup"><span data-stu-id="407ba-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 <span data-ttu-id="407ba-136">[!code-vb[VbVbalrMyResources #&14;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="407ba-136">[!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]</span></span>  
  
 <span data-ttu-id="407ba-137">為了讓範例能夠運作，您的應用程式必須`Nickname`類型設定`String`。</span><span class="sxs-lookup"><span data-stu-id="407ba-137">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407ba-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="407ba-138">See Also</span></span>  
 <span data-ttu-id="407ba-139"><xref:System.Configuration.ApplicationSettingsBase></xref:System.Configuration.ApplicationSettingsBase></span><span class="sxs-lookup"><span data-stu-id="407ba-139"><xref:System.Configuration.ApplicationSettingsBase></span></span>   
<span data-ttu-id="407ba-140"> [如何︰ 讀取 Visual Basic 中的應用程式設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span><span class="sxs-lookup"><span data-stu-id="407ba-140"> [How to: Read Application Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span></span>  
<span data-ttu-id="407ba-141"> [如何︰ 變更 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="407ba-141"> [How to: Change User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span></span>  
<span data-ttu-id="407ba-142"> [如何︰ 保存 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="407ba-142"> [How to: Persist User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span></span>  
<span data-ttu-id="407ba-143"> [如何︰ 建立 Visual Basic 中的使用者設定的屬性方格](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="407ba-143"> [How to: Create Property Grids for User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span></span>  
<span data-ttu-id="407ba-144"> [管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)</span><span class="sxs-lookup"><span data-stu-id="407ba-144"> [Managing Application Settings (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)</span></span>
