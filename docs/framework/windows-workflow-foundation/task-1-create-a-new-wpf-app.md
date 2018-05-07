---
title: 工作 1：建立新的 Windows Presentation Foundation 應用程式
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 5576d6f893aa405d454758387334b85a473b0c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>工作 1：建立新的 Windows Presentation Foundation 應用程式
在這項工作，您會建立空的 Windows Presentation Foundation (WPF) 應用程式使用的 WPF 應用程式的 Visual Studio 範本，並將參考加入至適當[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]工作流程組件。  
  
### <a name="to-create-the-wpf-application-project"></a>若要建立 WPF 應用程式專案  
  
1.  開啟 Visual Studio 以及**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在**新專案**對話方塊方塊中，選取  **Visual C#** 或**Visual Basic**從**已安裝的範本**的左側窗格方塊。 如果您選擇的語言沒有出現，查看 **其他語言**。  
  
3.  選取**Windows**中**已安裝的範本**窗格。  
  
4.  在上方窗格中，確認 （預設值） **.NET Framework 4**已選取下拉式清單方塊中，然後選取**WPF 應用程式**。  
  
5.  設定專案的名稱**HostingApplication**視窗的底部。  
  
6.  方案名稱設定為**RehostingTheDesigner**。  
  
7.  按一下**確定**建立應用程式專案。 Visual Studio 會建立基本 WPF UI 應用程式，並且包含適當的 XAML 和程式碼後置檔案。  
  
8.  將參考加入至**WorkflowModel**組件。 若要這樣做，請在**方案總管 中**，以滑鼠右鍵按一下**HostingApplication**專案，然後選取**加入參考**。  
  
9. 在**加入參考**對話方塊中，按一下  **.NET**索引標籤上，按住 CTRL 鍵，選取下列組件，，然後按一下**確定**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. 按一下 [確定 **Deploying Office Solutions**]。  
  
11. 請參閱[工作 2： 裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)以了解如何裝載工作流程設計工具設計畫布。  
  
## <a name="see-also"></a>另請參閱  
 [重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [工作 2：裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
