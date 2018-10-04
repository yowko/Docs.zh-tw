---
title: 移轉指引
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 73488354a807d8bf7d90c97b95f1021d884efd27
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777954"
---
# <a name="migration-guidance"></a>移轉指引
在  [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]，Microsoft 即將發行的第二個主要版本的 Windows Workflow Foundation (WF)。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 是在 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 中發佈 (其中包含 System.Workflow.* 命名空間中的型別；現在則是指 WF3)，並在 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 中增強。 WF3 也是屬於[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]，但它有與新的工作流程技術 (System.Activities。 中的型別\*命名空間; 以 WF4)。 在考量何時採用 WF4 時，重要的是要先了解到：您必須控制時機。  
  
-   WF3 是 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中受到完整支援的一部分。  
  
-   WF3 應用程式在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 上執行而不必修改，並繼續受到完整支援。  
  
-   您可以建立新的 WF3 應用程式和您現有的應用程式可編輯 Visual Studio 2012 中，而且完全支援。  
  
 因此，決定是否来採用.NET Framework 4 低耦合移至 WF4 （system.activities.*） 從 WF3 (System.Workflow。\*)。 這個主題會提供 WF 移轉指引的連結，此連結中提供使用 WF3 與 WF4 的相關資訊。  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>WF 移轉白皮書與做法指南  
 [WF 移轉概觀](https://go.microsoft.com/fwlink/?LinkId=153873)主題提供 WF3 和 WF4 以及移轉策略之間關係的廣泛概觀。 附隨的主題會深入查看特定主題。  
  
 [WF 移轉概觀](https://go.microsoft.com/fwlink/?LinkId=153873)  
 描述 WF3 與 WF4 之間的關係，以及您身為 .NET 4 工作流程技術之使用者或潛在使用者可做的選擇。  
  
 [WF 移轉： WF3 開發的最佳作法](https://go.microsoft.com/fwlink/?LinkId=153852)  
 討論如何設計 WF3 成品，以便更簡易地移轉為 WF4。  
  
 [WF 指引： 規則](https://go.microsoft.com/fwlink/?LinkId=153854)  
 討論如何進一步對 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 方案進行與規則相關的投資。  
  
 [WF 指引： 狀態機器](https://go.microsoft.com/fwlink/?LinkId=153855)  
 討論在缺乏狀態機器活動的情況下如何建立 WF4 控制流程的模型。  
  
 請注意，此指引只適用於以 .NET Framework 4 為目標的工作流程專案。 狀態機器工作流程已加入在含有 Platform Update 1 版本的 .NET 4.0.1 中，並且包含在 .NET Framework 4.5 中。 如需有關狀態機器工作流程，在.NET 4.0.1-4.0.3 以及.NET Framework 4.5 中，請參閱[Update 4.0.1 for Microsoft.NET Framework 4 功能](https://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc)並[狀態機器工作流程](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md)。  
  
 [WF 移轉做法指南： 自訂活動](https://go.microsoft.com/fwlink/?LinkId=153856)  
 提供在 WF4 上重新設計 WF3 自訂活動的範例與指引。  
  
 [WF 移轉做法指南： 進階自訂活動](https://go.microsoft.com/fwlink/?LinkId=275560)  
 提供重新設計進階 WF3 自訂活動的指引，這些活動會使用 WF3 佇列，並排定子活動做為 WF4 自訂活動。  
  
 [WF 移轉做法指南： 工作流程](https://go.microsoft.com/fwlink/?LinkId=153858)  
 提供在 WF4 上重新設計 WF3 的範例與指引。  
  
 [WF 移轉做法指南： 工作流程裝載](https://go.microsoft.com/fwlink/?LinkId=275561)  
 提供將 WF3 裝載程式碼重新設計成 WF4 裝載程式碼的指引。 目標是要彌補在工作流程中裝載 WF3 和 WF4 之間的主要差異。  
  
 [WF 移轉做法指南： 工作流程追蹤](https://go.microsoft.com/fwlink/?LinkId=275562)  
 提供使用對等 WF4 追蹤程式碼和組態，重新設計 WF3 追蹤程式碼和組態的指引。  
  
 [WF 指引： 工作流程服務](https://go.microsoft.com/fwlink/?LinkId=275564)  
 提供範例導向的逐步指示，示範如何針對全新活動的一般狀況，將實作 WF3 中建立之 Windows Communication Foundation (WCF) Web 服務 (通常稱為工作流程服務) 的工作流程，重新設計成使用 WF4。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Activities.Statements.Interop>
