---
title: 作法：建立自訂活動範本
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 4ec84658dbe3039a4d7d714f8da183e6a5eb6ca4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989717"
---
# <a name="how-to-create-a-custom-activity-template"></a>HOW TO：建立自訂活動範本

自訂活動範本是用來自訂活動的組態，包括自訂複合活動，因此使用者不需要個別建立每個活動以及手動設定其所有屬性和其他設定。 這些自訂範本可以在的 [**工具箱**] 中[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]或從重新裝載設計工具中取得，使用者可以從中將其拖曳至預先設定的設計介面。 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]附有這類範本的良好範例： [Sendandreceivereply 範本設計](/visualstudio/workflow-designer/sendandreceivereply-template-designer)工具和 [訊息活動設計](/visualstudio/workflow-designer/messaging-activity-designers)工具 分類中的 [receiveandsendreply 範本設計](/visualstudio/workflow-designer/receiveandsendreply-template-designer)工具。

 本主題中的第一個程式描述如何建立**延遲**活動的自訂活動範本，而第二個程式會簡要說明如何讓它在中[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]使用，以驗證自訂範本是否正常運作。

 自訂活動範本必須實作 <xref:System.Activities.Presentation.IActivityTemplateFactory>。 此介面有單一 <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> 方法，您可以用它來建立及設定範本中所用的活動執行個體。

## <a name="to-create-a-template-for-the-delay-activity"></a>若要建立 Delay 活動範本

1. 啟動 Visual Studio 2010。

2. 在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3. 在 [**專案類型**] 窗格中，根據您的語言喜好設定，從 [**視覺效果C#** 專案] 或 [ **Visual Basic** ] 群組選取 [**工作流程**]。

4. 在 [**範本**] 窗格中，選取 [**活動程式庫**]。

5. 在 [**名稱**] 方塊中`DelayActivityTemplate`，輸入。

6. 接受 [**位置**] 和 [**方案名稱**] 文字方塊中的預設值，然後按一下 **[確定]** 。

7. 在**方案總管**中，以滑鼠右鍵按一下 DelayActivityTemplate 專案的 [參考] 目錄，然後選擇 [**加入參考**] 以開啟 [**加入參考**] 對話方塊。

8. 移至 [ **.net** ] 索引標籤，然後從左側的 [**元件名稱**] 欄中選取 [ **PresentationFramework** ]，然後按一下 **[確定]** ，將參考加入至 PresentationFramework 檔。

9. 重複此程序，加入 System.Activities.Presentation.dll 和 WindowsBase.dll 檔案的參考。

10. 以滑鼠右鍵按一下**方案總管**中的 DelayActivityTemplate 專案，然後依序選擇 [**加入**] 和 [**新增專案**]，開啟 [**加入新專案**] 對話方塊。

11. 選取 [**類別**] 範本，將它命名為 MyDelayTemplate，然後按一下 **[確定]** 。

12. 開啟 MyDelayTemplate.cs 檔案，然後加入下列陳述式。

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. 使用具有下列程式碼的 <xref:System.Activities.Presentation.IActivityTemplateFactory> 類別來實作 `MyDelayActivity`。 這會將延遲設定擁有 10 秒持續時間。

    ```csharp
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

14. 從 [**建立**] 功能表中選取 [**建立方案**]，以產生 DelayActivityTemplate 檔案。

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>若要在工作流程設計工具中提供範本

1. 以滑鼠右鍵按一下**方案總管**中的 [DelayActivityTemplate] 方案，然後依序選擇 [**加入**] 和 [**新增專案**]，開啟 [**加入新的專案**] 對話方塊。

2. 選取 [**工作流程主控台應用程式**] 範本`CustomActivityTemplateApp`，將它命名為，然後按一下 **[確定]** 。

3. 在**方案總管**中，以滑鼠右鍵按一下 CustomActivityTemplateApp 專案的 [參考] 目錄，然後選擇 [**加入參考**] 以開啟 [**加入參考**] 對話方塊。

4. 移至 [**專案**] 索引標籤，然後從左側的 [**專案名稱**] 欄中選取 [ **DelayActivityTemplate** ]，然後按一下 **[確定]** ，將參考新增至您在第一個程式中建立的 DelayActivityTemplate 檔案。

5. 以滑鼠右鍵按一下**方案總管**中的 CustomActivityTemplateApp 專案，然後選擇 [**組建**] 以編譯應用程式。

6. 以滑鼠右鍵按一下**方案總管**中的 CustomActivityTemplateApp 專案，然後選擇 [**設定為啟始專案**]。

7. 從 [**調試**] 功能表中選取 [**啟動但不進行調試**]，然後在 cmd.exe 視窗中出現提示時，按任意鍵繼續進行。

8. 開啟 [Workflow1.xaml] 檔案，然後開啟 [**工具箱**]。

9. 在 [ **DelayActivityTemplate** ] 類別中找出 [ **MyDelayActivity** ] 範本。 將它拖曳至設計介面。 在 [**屬性**] 視窗`Duration`中確認屬性已設定為10秒。

## <a name="example"></a>範例
 MyDelayActivity.cs 檔案應該會包含下列程式碼。

```csharp
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

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [自訂工作流程設計體驗](customizing-the-workflow-design-experience.md)
