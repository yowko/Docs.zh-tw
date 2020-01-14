---
title: 移轉指導方針
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: f0c21d32b745a51bada9133230dd0c87be9c915e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937959"
---
# <a name="migration-guidance"></a>移轉指導方針

在 .NET Framework 4 中，Microsoft 會發行 Windows Workflow Foundation （WF）的第二個主要版本。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 已在 WinFX 中發行（這包括\* 命名空間中的類型，現在稱為 WF3），並在 .NET Framework 3.5 中增強。 WF3 也是 .NET Framework 4 的一部分，但是存在於新的工作流程技術（WF4 命名空間\* 中的類型，稱為）。 在考量何時採用 WF4 時，重要的是要先了解到：您必須控制時機。  
  
- WF3 是 .NET Framework 4 中受到完整支援的部分。  
  
- WF3 應用程式會在 .NET Framework 4 上執行，而不需修改，並繼續受到完整支援。  
  
- 您可以建立新的 WF3 應用程式，而且您現有的應用程式可以在 Visual Studio 2012 中編輯，而且完全受到支援。  
  
 因此，採用 .NET Framework 4 的決策會與您的決策分離，以從 WF3 （\*System.object）移至 WF4 （\*）。 這個主題會提供 WF 移轉指引的連結，此連結中提供使用 WF3 與 WF4 的相關資訊。  
  
## <a name="wf-migration-white-papers-and-cookbooks"></a>WF 遷移技術白皮書和操作手冊

 [WF 遷移總覽](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))主題提供 WF3 與 WF4 之間的關聯性，以及遷移策略的大致總覽。 附隨的主題會深入查看特定主題。  
  
 [WF 遷移總覽](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 描述 WF3 與 WF4 之間的關係，以及您身為 .NET 4 工作流程技術之使用者或潛在使用者可做的選擇。  
  
 [WF 遷移： WF3 開發的最佳做法](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 討論如何設計 WF3 成品，以便更簡易地移轉為 WF4。  
  
 [WF 指引：規則](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 討論如何將規則相關投資帶往 .NET Framework 4 個解決方案。  
  
 [WF 指引：狀態機器](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 討論在缺乏狀態機器活動的情況下如何建立 WF4 控制流程的模型。  
  
 請注意，此指引只適用於以 .NET Framework 4 為目標的工作流程專案。 狀態機器工作流程已加入在含有 Platform Update 1 版本的 .NET 4.0.1 中，並且包含在 .NET Framework 4.5 中。 如需 .NET 4.0.1-4.0.3 和 .NET Framework 4.5 中狀態機器工作流程的詳細資訊，請參閱[Update 4.0.1 For Microsoft .NET Framework 4 功能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100))和[狀態機器工作流程](state-machine-workflows.md)。  
  
 [WF 遷移操作手冊：自訂活動](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 提供在 WF4 上重新設計 WF3 自訂活動的範例與指引。  
  
 [WF 遷移操作手冊：先進的自訂活動](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 提供重新設計進階 WF3 自訂活動的指引，這些活動會使用 WF3 佇列，並排定子活動做為 WF4 自訂活動。  
  
 [WF 遷移操作手冊：工作流程](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 提供在 WF4 上重新設計 WF3 的範例與指引。  
  
 [WF 遷移操作手冊：工作流程裝載](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 提供將 WF3 裝載程式碼重新設計成 WF4 裝載程式碼的指引。 目標是要彌補在工作流程中裝載 WF3 和 WF4 之間的主要差異。  
  
 [WF 遷移操作手冊：工作流程追蹤](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 提供使用對等 WF4 追蹤程式碼和組態，重新設計 WF3 追蹤程式碼和組態的指引。  
  
 [WF 指引：工作流程服務](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 提供範例導向的逐步指示，示範如何針對全新活動的一般狀況，將實作 WF3 中建立之 Windows Communication Foundation (WCF) Web 服務 (通常稱為工作流程服務) 的工作流程，重新設計成使用 WF4。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Activities.Statements.Interop>
