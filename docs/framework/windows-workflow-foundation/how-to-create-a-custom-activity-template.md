---
title: HOW TO：建立自訂活動範本
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 87acf0d084154c9c3e5cbc97da4af9821709f0a5
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044836"
---
# <a name="how-to-create-a-custom-activity-template"></a>HOW TO：建立自訂活動範本

自訂活動範本是用來自訂活動的組態，包括自訂複合活動，因此使用者不需要個別建立每個活動以及手動設定其所有屬性和其他設定。 這些自訂範本以供在**工具箱**上[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]或重新裝載設計工具，從中使用者可以將它們拖曳到預先設定的設計介面。 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 隨附於這類範本的好例子： [SendAndReceiveReply 範本設計工具](/visualstudio/workflow-designer/sendandreceivereply-template-designer)並[ReceiveAndSendReply 範本設計工具](/visualstudio/workflow-designer/receiveandsendreply-template-designer)在[傳訊活動設計工具](/visualstudio/workflow-designer/messaging-activity-designers)類別。

 本主題中的第一個程序描述如何建立自訂活動範本**延遲**活動和第二個程序簡短描述如何使其可用於[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]驗證的自訂範本能運作。

 自訂活動範本必須實作 <xref:System.Activities.Presentation.IActivityTemplateFactory>。 此介面有單一 <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> 方法，您可以用它來建立及設定範本中所用的活動執行個體。

## <a name="to-create-a-template-for-the-delay-activity"></a>若要建立 Delay 活動範本

1.  啟動 Visual Studio 2010。

2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  在 **專案類型**窗格中，選取**工作流程**從**Visual C#** 專案或**Visual Basic**群組取決於您語言喜好設定。

4.  在 **範本**窗格中，選取**活動程式庫**。

5.  在 **名稱**方塊中，輸入`DelayActivityTemplate`。

6.  接受中的預設值**位置**並**方案名稱**文字方塊中，然後按一下 **確定**。

7.  以滑鼠右鍵按一下 DelayActivityTemplate 專案中的 [參考] 目錄**方案總管**，然後選擇 [**加入參考**以開啟**加入參考**] 對話方塊。

8.  移至 **.NET**索引標籤，然後選取**PresentationFramework**從**元件名稱**資料行，然後按一下**確定**加入的參考PresentationFramework.dll 檔案。

9. 重複此程序，加入 System.Activities.Presentation.dll 和 WindowsBase.dll 檔案的參考。

10. 以滑鼠右鍵按一下 DelayActivityTemplate 專案中的**方案總管**，然後選擇 [**新增**，然後**新項目**以開啟**加入新項目**] 對話方塊。

11. 選取 **類別**範本，它命名為 MyDelayTemplate，然後再按一下**確定**。

12. 開啟 MyDelayTemplate.cs 檔案，然後加入下列陳述式。

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. 使用具有下列程式碼的 <xref:System.Activities.Presentation.IActivityTemplateFactory> 類別來實作 `MyDelayActivity`。 這會將延遲設定擁有 10 秒持續時間。

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

14. 選取 **建置方案**從**建置**功能表以產生 DelayActivityTemplate.dll 檔案。

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>若要在工作流程設計工具中提供範本

1.  以滑鼠右鍵按一下 DelayActivityTemplate 方案，在**方案總管**，然後選擇 [**新增**，然後**新專案**以開啟**加入新的專案** ] 對話方塊。

2.  選取 **工作流程主控台應用程式**範本，其命名`CustomActivityTemplateApp`，然後按一下**確定**。

3.  以滑鼠右鍵按一下 CustomActivityTemplateApp 專案中的 [參考] 目錄**方案總管**，然後選擇**加入參考**以開啟**加入參考**對話方塊方塊。

4.  移至**專案**索引標籤，然後選取**DelayActivityTemplate**從**專案名稱**資料行，然後按一下**確定**新增參考您在第一個程序中建立之 DelayActivityTemplate.dll 檔案。

5.  以滑鼠右鍵按一下 CustomActivityTemplateApp 專案中的**方案總管**，然後選擇**建置**編譯應用程式。

6.  以滑鼠右鍵按一下 CustomActivityTemplateApp 專案中的**方案總管**，然後選擇**設定為啟始專案**。

7.  選取 **啟動但不偵錯**從**偵錯**功能表，然後按下任何鍵繼續時提示您在 cmd.exe 視窗中。

8.  開啟 Workflow1.xaml 檔案，然後開啟**工具箱**。

9. 找出**Delayactivitytemplate**中的範本**DelayActivityTemplate**類別目錄。 將它拖曳至設計介面。 在 [確認**屬性**] 視窗，`Duration`屬性設定為 10 秒。

## <a name="example"></a>範例
 MyDelayActivity.cs 檔案應該會包含下列程式碼。

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

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [自訂工作流程設計體驗](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)