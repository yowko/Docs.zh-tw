---
title: 在工作流程方案中加入服務參考
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 1b4cc16d3bd85c28ac7267e88ae0a714620c9861
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557054"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>在工作流程方案中加入服務參考

在工作流程應用程式中加入服務參考的運作方式與在一般 WCF 應用程式中加入服務參考的運作方式稍有不同。 當您選取 [**加入**  >  **服務參考**] 並指定服務的 URL 時，會下載中繼資料並產生自訂活動，讓您能夠呼叫 wcf 服務或 wcf workflow service。 加入服務參考之後，重建方案，因而建置所產生的活動。 接著，這些活動會出現在工作流程設計工具工具箱中。 只有當您要在工作流程方案中新增服務參考時，才能使用此方法。 下列 web 轉換顯示如何在其他類型的專案中加入服務參考： [從 Web 專案中的工作流程呼叫 WCF 服務](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)。

將兩個或多個服務參考加入至包含相同作業名稱的服務將會造成問題。 產生的活動只會呼叫第一個服務作業。 若要解決此問題，請重新命名服務作業，使其不同，或變更每個產生之活動內的端點設定名稱。

## <a name="see-also"></a>另請參閱

- [工作流程服務](workflow-services.md)
- [從 Web 專案的工作流程中呼叫 WCF 服務](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
