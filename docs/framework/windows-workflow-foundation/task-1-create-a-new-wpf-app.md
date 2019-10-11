---
title: 工作 1：建立新的 Windows Presentation Foundation 應用程式
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031890"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>工作 1：建立新的 Windows Presentation Foundation 應用程式

在這項工作中，您將使用 WPF 應用程式 Visual Studio 範本來建立空的 Windows Presentation Foundation （WPF）應用程式，並將參考新增至適當的 @no__t 0 工作流程元件。  
  
## <a name="to-create-the-wpf-application-project"></a>若要建立 WPF 應用程式專案

1. 開啟 Visual Studio，並在 **[檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。

2. 在 [**新增專案**] 對話方塊中，從方塊左側的 [**已安裝的範本**] 窗格中，選取 [**視覺C#效果**] 或 [ **Visual Basic** ]。 如果未出現您選擇的語言，請查看 [**其他語言**]。

3. 在 [**已安裝的範本**] 窗格中選取 [ **Windows** ]。

4. 在上方窗格中，確認已在下拉式清單方塊中選取 [ **.NET Framework 4** ] （預設值），然後選取 [ **WPF 應用程式**]。

5. 在視窗底部，將專案的名稱設定為**HostingApplication** 。

6. 將 [方案名稱] 設定為**設定為 rehostingthedesigner**。

7. 按一下 **[確定]** 以建立應用程式專案。 Visual Studio 會為您的應用程式建立基本 WPF UI，並且包含適當的 XAML 和程式碼後置檔案。

8. 新增**WorkflowModel**元件的參考。 若要這麼做，請在**方案總管**中，以滑鼠右鍵按一下**HostingApplication**專案，然後選取 [**加入參考**]。

9. 在 [**加入參考**] 對話方塊中，按一下 [ **.net** ] 索引標籤，按住 CTRL 鍵，選取下列元件，然後按一下 **[確定]** ：

    - System.Activities
    - System.Activities.Presentation
    - System.Activities.Core.Presentation

10. 請參閱 [Task 2：裝載工作流程設計工具 @ no__t-0，以瞭解如何裝載工作流程設計工具設計畫布。

## <a name="see-also"></a>另請參閱

- [重新裝載工作流程設計工具](rehosting-the-workflow-designer.md)
- [Task 2：裝載工作流程設計工具 @ no__t-0
