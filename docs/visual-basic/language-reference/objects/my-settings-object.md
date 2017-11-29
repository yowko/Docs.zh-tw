---
title: "My.Settings 物件"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords: My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f744460f8ea6c6c7f5c8c5e1658bd357e910def
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mysettings-object"></a><span data-ttu-id="c77b7-102">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="c77b7-102">My.Settings Object</span></span>
<span data-ttu-id="c77b7-103">提供屬性和方法來存取應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="c77b7-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c77b7-104">備註</span><span class="sxs-lookup"><span data-stu-id="c77b7-104">Remarks</span></span>  
 <span data-ttu-id="c77b7-105">`My.Settings`物件存取應用程式的設定，並可讓您動態儲存及擷取屬性設定和應用程式的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="c77b7-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="c77b7-106">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="c77b7-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c77b7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c77b7-107">Properties</span></span>  
 <span data-ttu-id="c77b7-108">`My.Settings` 物件的屬性可存取您應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="c77b7-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="c77b7-109">若要新增或移除設定，使用**設定設計工具**。</span><span class="sxs-lookup"><span data-stu-id="c77b7-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="c77b7-110">每個設定都**名稱**，**類型**，**範圍**，和**值**，以及這些設定會決定如何存取每個設定的屬性會出現在`My.Settings`物件：</span><span class="sxs-lookup"><span data-stu-id="c77b7-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="c77b7-111">**名稱**判斷屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="c77b7-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="c77b7-112">**型別**判斷屬性的型別。</span><span class="sxs-lookup"><span data-stu-id="c77b7-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="c77b7-113">**範圍**指出屬性是否為唯讀。</span><span class="sxs-lookup"><span data-stu-id="c77b7-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="c77b7-114">如果值為**應用程式**，屬性是唯讀的; 如果值為**使用者**，屬性是讀寫。</span><span class="sxs-lookup"><span data-stu-id="c77b7-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="c77b7-115">**值**是屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="c77b7-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c77b7-116">方法</span><span class="sxs-lookup"><span data-stu-id="c77b7-116">Methods</span></span>  
  
|<span data-ttu-id="c77b7-117">方法</span><span class="sxs-lookup"><span data-stu-id="c77b7-117">Method</span></span>|<span data-ttu-id="c77b7-118">說明</span><span class="sxs-lookup"><span data-stu-id="c77b7-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="c77b7-119">重新載入使用者設定，從上次儲存的值。</span><span class="sxs-lookup"><span data-stu-id="c77b7-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="c77b7-120">儲存目前的使用者設定。</span><span class="sxs-lookup"><span data-stu-id="c77b7-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="c77b7-121">`My.Settings`物件也提供進階的屬性和方法，繼承自<xref:System.Configuration.ApplicationSettingsBase>類別。</span><span class="sxs-lookup"><span data-stu-id="c77b7-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c77b7-122">工作</span><span class="sxs-lookup"><span data-stu-id="c77b7-122">Tasks</span></span>  
 <span data-ttu-id="c77b7-123">下表列出包含工作的範例`My.Settings`物件。</span><span class="sxs-lookup"><span data-stu-id="c77b7-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="c77b7-124">以</span><span class="sxs-lookup"><span data-stu-id="c77b7-124">To</span></span>|<span data-ttu-id="c77b7-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="c77b7-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="c77b7-126">讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-126">Read an application setting</span></span>|[<span data-ttu-id="c77b7-127">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="c77b7-128">變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-128">Change a user setting</span></span>|[<span data-ttu-id="c77b7-129">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="c77b7-130">保存使用者設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-130">Persist user settings</span></span>|[<span data-ttu-id="c77b7-131">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="c77b7-132">建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="c77b7-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="c77b7-133">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="c77b7-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="c77b7-134">範例</span><span class="sxs-lookup"><span data-stu-id="c77b7-134">Example</span></span>  
 <span data-ttu-id="c77b7-135">此範例會顯示 `Nickname` 設定的值。</span><span class="sxs-lookup"><span data-stu-id="c77b7-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 <span data-ttu-id="c77b7-136">為了確保此範例正常運作，您的應用程式必須具有 `String` 類型的 `Nickname` 設定。</span><span class="sxs-lookup"><span data-stu-id="c77b7-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77b7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c77b7-137">See Also</span></span>  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [<span data-ttu-id="c77b7-138">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="c77b7-139">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="c77b7-140">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="c77b7-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="c77b7-141">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="c77b7-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="c77b7-142">管理應用程式設定 (.NET)</span><span class="sxs-lookup"><span data-stu-id="c77b7-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
