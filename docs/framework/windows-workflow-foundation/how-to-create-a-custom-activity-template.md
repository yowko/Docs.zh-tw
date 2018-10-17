---
title: HOW TO：建立自訂活動範本
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 87acf0d084154c9c3e5cbc97da4af9821709f0a5
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372105"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="4f0ad-102">HOW TO：建立自訂活動範本</span><span class="sxs-lookup"><span data-stu-id="4f0ad-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="4f0ad-103">自訂活動範本是用來自訂活動的組態，包括自訂複合活動，因此使用者不需要個別建立每個活動以及手動設定其所有屬性和其他設定。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="4f0ad-104">這些自訂範本以供在**工具箱**上[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]或重新裝載設計工具，從中使用者可以將它們拖曳到預先設定的設計介面。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] <span data-ttu-id="4f0ad-105">隨附於這類範本的好例子： [SendAndReceiveReply 範本設計工具](/visualstudio/workflow-designer/sendandreceivereply-template-designer)並[ReceiveAndSendReply 範本設計工具](/visualstudio/workflow-designer/receiveandsendreply-template-designer)在[傳訊活動設計工具](/visualstudio/workflow-designer/messaging-activity-designers)類別。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-105">ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="4f0ad-106">本主題中的第一個程序描述如何建立自訂活動範本**延遲**活動和第二個程序簡短描述如何使其可用於[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]驗證的自訂範本能運作。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>

 <span data-ttu-id="4f0ad-107">自訂活動範本必須實作 <xref:System.Activities.Presentation.IActivityTemplateFactory>。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="4f0ad-108">此介面有單一 <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> 方法，您可以用它來建立及設定範本中所用的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="4f0ad-109">若要建立 Delay 活動範本</span><span class="sxs-lookup"><span data-stu-id="4f0ad-109">To create a template for the Delay activity</span></span>

1.  <span data-ttu-id="4f0ad-110">啟動 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-110">Start Visual Studio 2010.</span></span>

2.  <span data-ttu-id="4f0ad-111">在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="4f0ad-112">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-112">The **New Project** dialog box opens.</span></span>

3.  <span data-ttu-id="4f0ad-113">在 **專案類型**窗格中，選取**工作流程**從**Visual C#** 專案或**Visual Basic**群組取決於您語言喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4.  <span data-ttu-id="4f0ad-114">在 **範本**窗格中，選取**活動程式庫**。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-114">In the **Templates** pane, select **Activity Library**.</span></span>

5.  <span data-ttu-id="4f0ad-115">在 **名稱**方塊中，輸入`DelayActivityTemplate`。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6.  <span data-ttu-id="4f0ad-116">接受中的預設值**位置**並**方案名稱**文字方塊中，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7.  <span data-ttu-id="4f0ad-117">以滑鼠右鍵按一下 DelayActivityTemplate 專案中的 [參考] 目錄**方案總管**，然後選擇 [**加入參考**以開啟**加入參考**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8.  <span data-ttu-id="4f0ad-118">移至 **.NET**索引標籤，然後選取**PresentationFramework**從**元件名稱**資料行，然後按一下**確定**加入的參考PresentationFramework.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="4f0ad-119">重複此程序，加入 System.Activities.Presentation.dll 和 WindowsBase.dll 檔案的參考。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="4f0ad-120">以滑鼠右鍵按一下 DelayActivityTemplate 專案中的**方案總管**，然後選擇 [**新增**，然後**新項目**以開啟**加入新項目**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="4f0ad-121">選取 **類別**範本，它命名為 MyDelayTemplate，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="4f0ad-122">開啟 MyDelayTemplate.cs 檔案，然後加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="4f0ad-123">使用具有下列程式碼的 <xref:System.Activities.Presentation.IActivityTemplateFactory> 類別來實作 `MyDelayActivity`。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="4f0ad-124">這會將延遲設定擁有 10 秒持續時間。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. <span data-ttu-id="4f0ad-125">選取 **建置方案**從**建置**功能表以產生 DelayActivityTemplate.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="4f0ad-126">若要在工作流程設計工具中提供範本</span><span class="sxs-lookup"><span data-stu-id="4f0ad-126">To make the template available in a Workflow Designer</span></span>

1.  <span data-ttu-id="4f0ad-127">以滑鼠右鍵按一下 DelayActivityTemplate 方案，在**方案總管**，然後選擇 [**新增**，然後**新專案**以開啟**加入新的專案** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2.  <span data-ttu-id="4f0ad-128">選取 **工作流程主控台應用程式**範本，其命名`CustomActivityTemplateApp`，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3.  <span data-ttu-id="4f0ad-129">以滑鼠右鍵按一下 CustomActivityTemplateApp 專案中的 [參考] 目錄**方案總管**，然後選擇**加入參考**以開啟**加入參考**對話方塊方塊。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4.  <span data-ttu-id="4f0ad-130">移至**專案**索引標籤，然後選取**DelayActivityTemplate**從**專案名稱**資料行，然後按一下**確定**新增參考您在第一個程序中建立之 DelayActivityTemplate.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5.  <span data-ttu-id="4f0ad-131">以滑鼠右鍵按一下 CustomActivityTemplateApp 專案中的**方案總管**，然後選擇**建置**編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6.  <span data-ttu-id="4f0ad-132">以滑鼠右鍵按一下 CustomActivityTemplateApp 專案中的**方案總管**，然後選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7.  <span data-ttu-id="4f0ad-133">選取 **啟動但不偵錯**從**偵錯**功能表，然後按下任何鍵繼續時提示您在 cmd.exe 視窗中。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8.  <span data-ttu-id="4f0ad-134">開啟 Workflow1.xaml 檔案，然後開啟**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="4f0ad-135">找出**Delayactivitytemplate**中的範本**DelayActivityTemplate**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="4f0ad-136">將它拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-136">Drag it onto the design surface.</span></span> <span data-ttu-id="4f0ad-137">在 [確認**屬性**] 視窗，`Duration`屬性設定為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="4f0ad-138">範例</span><span class="sxs-lookup"><span data-stu-id="4f0ad-138">Example</span></span>
 <span data-ttu-id="4f0ad-139">MyDelayActivity.cs 檔案應該會包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f0ad-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="4f0ad-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f0ad-140">See Also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="4f0ad-141">自訂工作流程設計體驗</span><span class="sxs-lookup"><span data-stu-id="4f0ad-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)