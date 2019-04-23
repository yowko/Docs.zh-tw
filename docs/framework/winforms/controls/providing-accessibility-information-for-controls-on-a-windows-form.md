---
title: 為 Windows Form 上的控制項提供可及性資訊
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 0f589f37d79c9ec8d55153aac4c846726a379055
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218325"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="0a151-102">為 Windows Form 上的控制項提供可及性資訊</span><span class="sxs-lookup"><span data-stu-id="0a151-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="0a151-103">協助工具是特製化的程式和裝置，可以協助殘障人士更有效地使用電腦。</span><span class="sxs-lookup"><span data-stu-id="0a151-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="0a151-104">範例包括針對視障人士的螢幕助讀程式，以及提供口頭指令，而不是使用滑鼠或鍵盤的人所適用的語音輸入公用程式。</span><span class="sxs-lookup"><span data-stu-id="0a151-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="0a151-105">這些協助工具會與 Windows Forms 控制項所公開的協助工具屬性互動。</span><span class="sxs-lookup"><span data-stu-id="0a151-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="0a151-106">這些屬性是：</span><span class="sxs-lookup"><span data-stu-id="0a151-106">These properties are:</span></span>  
  
-   <span data-ttu-id="0a151-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="0a151-107">**AccessibilityObject**</span></span>  
  
-   <span data-ttu-id="0a151-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="0a151-108">**AccessibleDefaultActionDescription**</span></span>  
  
-   <span data-ttu-id="0a151-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="0a151-109">**AccessibleDescription**</span></span>  
  
-   <span data-ttu-id="0a151-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="0a151-110">**AccessibleName**</span></span>  
  
-   <span data-ttu-id="0a151-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="0a151-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="0a151-112">AccessibilityObject 屬性</span><span class="sxs-lookup"><span data-stu-id="0a151-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="0a151-113">這個唯讀屬性包含 <xref:System.Windows.Forms.AccessibleObject> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a151-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="0a151-114">**AccessibleObject** 實作 <xref:Accessibility.IAccessible> 介面，它提供控制項的描述、螢幕位置、瀏覽功能和值等相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0a151-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="0a151-115">當控制項加入表單中時，設計工具會設定此值。</span><span class="sxs-lookup"><span data-stu-id="0a151-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="0a151-116">AccessibleDefaultActionDescription 屬性</span><span class="sxs-lookup"><span data-stu-id="0a151-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="0a151-117">這個字串描述控制項的動作。</span><span class="sxs-lookup"><span data-stu-id="0a151-117">This string describes the action of the control.</span></span> <span data-ttu-id="0a151-118">它不會出現在 [屬性] 視窗中，並且只能在程式碼中設定。</span><span class="sxs-lookup"><span data-stu-id="0a151-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="0a151-119">下列範例會為按鈕控制項設定此屬性：</span><span class="sxs-lookup"><span data-stu-id="0a151-119">The following example sets this property for a button control:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="0a151-120">AccessibleDescription 屬性</span><span class="sxs-lookup"><span data-stu-id="0a151-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="0a151-121">這個字串描述控制項。</span><span class="sxs-lookup"><span data-stu-id="0a151-121">This string describes the control.</span></span> <span data-ttu-id="0a151-122">它可能在 [屬性] 視窗或在程式碼中設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0a151-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="0a151-123">AccessibleName 屬性</span><span class="sxs-lookup"><span data-stu-id="0a151-123">AccessibleName Property</span></span>  
 <span data-ttu-id="0a151-124">這是報告給協助工具輔助的控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="0a151-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="0a151-125">它可能在 [屬性] 視窗或在程式碼中設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0a151-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="0a151-126">AccessibleRole 屬性</span><span class="sxs-lookup"><span data-stu-id="0a151-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="0a151-127">此屬性，其中包含 <xref:System.Windows.Forms.AccessibleRole> 列舉，描述控制項的使用者介面角色。</span><span class="sxs-lookup"><span data-stu-id="0a151-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="0a151-128">新控制項的值會設定為 `Default`。</span><span class="sxs-lookup"><span data-stu-id="0a151-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="0a151-129">這表示，根據預設， **Button** 控制項可當做 **Button**。</span><span class="sxs-lookup"><span data-stu-id="0a151-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="0a151-130">如果控制項具有另一個角色，您可能會想重設這個屬性。</span><span class="sxs-lookup"><span data-stu-id="0a151-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="0a151-131">例如，您可能使用 **PictureBox** 控制項作為 **Chart**，而您想要協助工具輔助將角色報告為 **Chart**，不是 **PictureBox**。</span><span class="sxs-lookup"><span data-stu-id="0a151-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="0a151-132">您也可能想要為您開發的自訂控制項指定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="0a151-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="0a151-133">這個屬性可能在 [屬性] 視窗或在程式碼中設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0a151-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a151-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a151-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
