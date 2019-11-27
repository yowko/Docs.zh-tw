---
title: My.Settings 物件
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350350"
---
# <a name="mysettings-object"></a><span data-ttu-id="588de-102">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="588de-102">My.Settings Object</span></span>
<span data-ttu-id="588de-103">提供用來存取應用程式設定的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="588de-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="588de-104">備註</span><span class="sxs-lookup"><span data-stu-id="588de-104">Remarks</span></span>  
 <span data-ttu-id="588de-105">`My.Settings` 物件可讓您存取應用程式的設定，並可讓您以動態方式儲存和抓取應用程式的屬性設定和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="588de-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="588de-106">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="588de-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="588de-107">屬性</span><span class="sxs-lookup"><span data-stu-id="588de-107">Properties</span></span>  
 <span data-ttu-id="588de-108">`My.Settings` 物件的屬性可存取您應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="588de-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="588de-109">若要新增或移除設定，請使用 [**設定設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="588de-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="588de-110">每個設定都有 [**名稱**]、[**類型**]、[**範圍**] 和 [**值**]，而這些設定會決定存取每個設定的屬性如何出現在 `My.Settings` 物件中：</span><span class="sxs-lookup"><span data-stu-id="588de-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="588de-111">**名稱**決定屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="588de-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="588de-112">**類型**決定屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="588de-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="588de-113">**範圍**指出屬性是否為唯讀。</span><span class="sxs-lookup"><span data-stu-id="588de-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="588de-114">如果值為**Application**，則屬性為唯讀;如果值為**User**，則屬性為讀寫。</span><span class="sxs-lookup"><span data-stu-id="588de-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="588de-115">**Value**是屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="588de-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="588de-116">方法</span><span class="sxs-lookup"><span data-stu-id="588de-116">Methods</span></span>  
  
|<span data-ttu-id="588de-117">方法</span><span class="sxs-lookup"><span data-stu-id="588de-117">Method</span></span>|<span data-ttu-id="588de-118">描述</span><span class="sxs-lookup"><span data-stu-id="588de-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="588de-119">從上次儲存的值重載使用者設定。</span><span class="sxs-lookup"><span data-stu-id="588de-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="588de-120">儲存目前的使用者設定。</span><span class="sxs-lookup"><span data-stu-id="588de-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="588de-121">`My.Settings` 物件也提供從 <xref:System.Configuration.ApplicationSettingsBase> 類別繼承的先進屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="588de-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="588de-122">工作</span><span class="sxs-lookup"><span data-stu-id="588de-122">Tasks</span></span>  
 <span data-ttu-id="588de-123">下表列出涉及 `My.Settings` 物件的工作範例。</span><span class="sxs-lookup"><span data-stu-id="588de-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="588de-124">進行</span><span class="sxs-lookup"><span data-stu-id="588de-124">To</span></span>|<span data-ttu-id="588de-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="588de-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="588de-126">讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="588de-126">Read an application setting</span></span>|[<span data-ttu-id="588de-127">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="588de-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="588de-128">變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="588de-128">Change a user setting</span></span>|[<span data-ttu-id="588de-129">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="588de-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="588de-130">保存使用者設定</span><span class="sxs-lookup"><span data-stu-id="588de-130">Persist user settings</span></span>|[<span data-ttu-id="588de-131">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="588de-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="588de-132">建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="588de-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="588de-133">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="588de-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="588de-134">範例</span><span class="sxs-lookup"><span data-stu-id="588de-134">Example</span></span>  
 <span data-ttu-id="588de-135">此範例會顯示 `Nickname` 設定的值。</span><span class="sxs-lookup"><span data-stu-id="588de-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="588de-136">為了確保此範例正常運作，您的應用程式必須具有 `Nickname` 類型的 `String` 設定。</span><span class="sxs-lookup"><span data-stu-id="588de-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="588de-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="588de-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="588de-138">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="588de-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="588de-139">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="588de-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="588de-140">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="588de-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="588de-141">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="588de-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="588de-142">管理應用程式設定 (.NET)</span><span class="sxs-lookup"><span data-stu-id="588de-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
