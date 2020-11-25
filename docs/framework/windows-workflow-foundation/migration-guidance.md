---
title: 移轉指引
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: b9b90aedc06fb4a4564596d61aa0ac2dc4c6143f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733590"
---
# <a name="migration-guidance"></a>移轉指引

在 .NET Framework 4 中，Microsoft 會發行 Windows Workflow Foundation (WF) 的第二個主要版本。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 已在 WinFX 中發行 (這包含了系統中的類型。 \* 命名現在稱為 WF3) ，並在 .NET Framework 3.5 中增強。 WF3 也是 .NET Framework 4 的一部分，但是存在於新的工作流程技術 (系統中的類型。 \* 命名稱為 WF4) 。 在考量何時採用 WF4 時，重要的是要先了解到：您必須控制時機。

- WF3 是 .NET Framework 4 的完整支援部分。

- WF3 應用程式不需修改即可在 .NET Framework 4 上執行，而且會繼續受到完整支援。

- 您可以建立新的 WF3 應用程式，而且您可以在 Visual Studio 2012 中編輯現有的應用程式，並受到完整支援。

 因此，採用 .NET Framework 4 的決策會與您的決策分離，以移至 WF4 (系統。 \*) 從 WF3 (System.object。 \*) 。 這個主題會提供 WF 移轉指引的連結，此連結中提供使用 WF3 與 WF4 的相關資訊。

## <a name="wf-migration-white-papers-and-cookbooks"></a>WF 遷移白皮書和操作手冊

 [WF 遷移總覽](/previous-versions/appfabric/ff383417(v=azure.10))主題提供 WF3 與 WF4 與遷移策略之間關聯性的廣泛總覽。 附隨的主題會深入查看特定主題。

 [WF 遷移總覽](/previous-versions/appfabric/ff383417(v=azure.10)) 描述 WF3 和 WF4 之間的關聯性，以及您在 .NET Framework 4 中作為使用者或工作流程技術潛在使用者的選擇。

 [WF 遷移： WF3 開發的最佳作法](/previous-versions/appfabric/ff383417(v=azure.10)) 討論如何設計 WF3 構件，以便更輕鬆地將它們遷移至 WF4。

 [WF 指引：規則](/previous-versions/appfabric/ff383417(v=azure.10)) 討論如何將規則相關投資帶到 .NET Framework 4 解決方案中。

 [WF 指引：狀態機器](/previous-versions/appfabric/ff383417(v=azure.10)) 討論 WF4 的控制流程模型（如果沒有 State-Machine 活動）。

 請注意，此指引只適用於以 .NET Framework 4 為目標的工作流程專案。 狀態機器工作流程已新增至 4.0.1 Platform Update 1 版本的 .NET Framework，並包含在 .NET Framework 4.5 中。 如需有關 .NET Framework 4.0.1-4.0.3 和 .NET Framework 4.5 中狀態機器工作流程的詳細資訊，請參閱 [Microsoft .NET Framework 4 功能](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) 和 [狀態機器工作流程](state-machine-workflows.md)的更新4.0.1。

 [WF 遷移手冊：自訂活動](/previous-versions/appfabric/ff383417(v=azure.10)) 提供在 WF4 上重新設計 WF3 自訂活動的範例和指示。

 [WF 遷移操作手冊： Advanced Custom 活動](/previous-versions/appfabric/ff383417(v=azure.10)) 提供重新設計 WF3 自訂活動的指導方針，這些活動會使用 WF3 佇列，並將子活動排程為 WF4 的自訂活動。

 [WF 遷移操作手冊：工作流程](/previous-versions/appfabric/ff383417(v=azure.10)) 提供在 WF4 上重新設計 WF3 工作流程的範例和指示。

 [WF 遷移操作手冊：工作流程裝載](/previous-versions/appfabric/ff383417(v=azure.10)) 提供將 WF3 裝載程式碼重新設計為 WF4 裝載程式碼的指引。 目標是要彌補在工作流程中裝載 WF3 和 WF4 之間的主要差異。

 [WF 遷移操作手冊：工作流程追蹤](/previous-versions/appfabric/ff383417(v=azure.10)) 提供使用對等 WF4 追蹤程式碼和設定來重新設計 WF3 追蹤程式碼和設定的指導方針。

 [WF 指引：工作流程服務](/previous-versions/appfabric/ff383417(v=azure.10)) 提供以範例為導向的逐步指示，可讓您重新設計 Windows Communication Foundation (WCF) web 服務的工作流程， (通常稱為工作流程服務) 在 WF3 中建立以使用 WF4，適用于現成活動的常見案例。

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Interop>
