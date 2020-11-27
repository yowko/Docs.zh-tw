---
title: 作法：建立自訂活動範本
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 90a54806833ff66797fb7beaa6ac8a912665bddc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280113"
---
# <a name="how-to-create-a-custom-activity-template"></a>作法：建立自訂活動範本

自訂活動範本是用來自訂活動的組態，包括自訂複合活動，因此使用者不需要個別建立每個活動以及手動設定其所有屬性和其他設定。 這些自訂範本可在 Windows 工作流程設計工具上的 [工具箱] 中或從重新裝載表設計 **工具** 中取得，使用者可以從中將它們拖曳到預先設定的設計介面。 工作流程設計工具隨附了這類範本的良好範例： [ [SendAndReceiveReply 範本設計](/visualstudio/workflow-designer/sendandreceivereply-template-designer)工具] 和 [[訊息活動設計](/visualstudio/workflow-designer/messaging-activity-designers)工具] 類別中的 [ [receiveandsendreply] 範本設計](/visualstudio/workflow-designer/receiveandsendreply-template-designer)工具]。

 本主題的第一個程式描述如何建立 **Delay** 活動的自訂活動範本，第二個程式會簡短說明如何將它提供給工作流程設計工具，以確認自訂範本可以運作。

 自訂活動範本必須實作 <xref:System.Activities.Presentation.IActivityTemplateFactory>。 此介面有單一 <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> 方法，您可以用它來建立及設定範本中所用的活動執行個體。

## <a name="to-create-a-template-for-the-delay-activity"></a>若要建立 Delay 活動範本

1. 啟動 Visual Studio 2010。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]**，再選取 **[專案]**。

     此時會開啟 [新增專案] 對話方塊。

3. 在 [**專案類型**] 窗格中，根據您的語言喜好設定，選取 **Visual c #** 專案或 **Visual Basic** 群組中的 **工作流程**。

4. 在 [ **範本** ] 窗格中，選取 [ **活動程式庫**]。

5. 在 [名稱]  方塊中，輸入 `DelayActivityTemplate`。

6. 接受 [ **位置** ] 和 [ **方案名稱** ] 文字方塊中的預設值，然後按一下 **[確定]**。

7. 在 **方案總管** 中，以滑鼠右鍵按一下 DelayActivityTemplate 專案的 [參考] 目錄，然後選擇 [ **加入參考** ] 以開啟 [ **加入參考** ] 對話方塊。

8. 移至 [ **.net** ] 索引標籤，然後從左側的 [**元件名稱**] 欄中選取 [ **PresentationFramework** ]，然後按一下 **[確定]** 以加入 PresentationFramework.dll 檔案的參考。

9. 重複此程序，加入 System.Activities.Presentation.dll 和 WindowsBase.dll 檔案的參考。

10. 在 **方案總管** 中，以滑鼠右鍵按一下 DelayActivityTemplate 專案，然後依序選擇 [ **加入** ] 和 [ **新增專案** ]，以開啟 [ **加入新專案** ] 對話方塊。

11. 選取 [ **類別** ] 範本，將它命名為 MyDelayTemplate，然後按一下 **[確定]**。

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

14. 從 [**組建**] 功能表選取 [**建立方案**]，以產生 DelayActivityTemplate.dll 檔案。

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>若要在工作流程設計工具中提供範本

1. 在 **方案總管** 中，以滑鼠右鍵按一下 DelayActivityTemplate 方案，然後依序選擇 [ **加入** ] 和 [ **新增專案** ]，以開啟 [ **加入新專案** ] 對話方塊。

2. 選取 [ **工作流程主控台應用程式** ] 範本，將它命名為 `CustomActivityTemplateApp` ，然後按一下 **[確定]**。

3. 在 **方案總管** 中，以滑鼠右鍵按一下 CustomActivityTemplateApp 專案的 [參考] 目錄，然後選擇 [ **加入參考** ] 以開啟 [ **加入參考** ] 對話方塊。

4. 移至 [**專案**] 索引標籤，然後從左側的 [**專案名稱**] 欄中選取 [ **DelayActivityTemplate** ]，然後按一下 **[確定]** ，將參考新增至您在第一個程式中建立的 DelayActivityTemplate.dll 檔案。

5. 在 **方案總管** 中，以滑鼠右鍵按一下 CustomActivityTemplateApp 專案，然後選擇 [ **組建** ] 以編譯應用程式。

6. 在 **方案總管** 中，以滑鼠右鍵按一下 CustomActivityTemplateApp 專案，然後選擇 [ **設定為啟始專案**]。

7. 從 [**調試**] 功能表選取 [**啟動但不進行調試**]，然後在 cmd.exe 視窗出現提示時，按任意鍵繼續。

8. 開啟 Workflow1.xaml .xaml 檔案，然後開啟 [ **工具箱**]。

9. 在 **DelayActivityTemplate** 類別中找出 **MyDelayActivity** 範本。 將它拖曳至設計介面。 在 [ **屬性** ] 視窗中確認 `Duration` 屬性已設定為10秒。

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
- [自訂工作流程設計經驗](customizing-the-workflow-design-experience.md)
