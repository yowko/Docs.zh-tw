---
title: 在工作流程方案中加入服務參考
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 9dcbf779d948f6d295c2a23f5a09efc5ac989cdd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869541"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>在工作流程方案中加入服務參考

在工作流程應用程式中加入服務參考的運作方式與在一般 WCF 應用程式中加入服務參考的運作方式稍有不同。 當您選取**新增 > 服務參考**服務的 URL，在下載中繼資料並指定自訂活動會產生可讓您呼叫 WCF 服務或 WCF 工作流程服務加入的參考。 加入服務參考之後，重建方案，因而建置所產生的活動。 接著，這些活動會出現在工作流程設計工具工具箱中。 但是請注意，只有在您於工作流程方案中加入服務參考時，這才有作用。 以下的網路廣播示範如何將服務參考加入其他專案類型：[從 Web 專案中的工作流程中呼叫 WCF 服務](https://go.microsoft.com/fwlink/?LinkId=207725)。

將兩個或多個服務參考加入至包含相同作業名稱的服務將會造成問題。 產生的活動只會呼叫第一個服務作業。 若要解決這個問題，請重新命名服務作業，使它們不相同，或在每個產生的活動中變更端點組態名稱。

## <a name="see-also"></a>另請參閱

- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [如何：建立會呼叫其他工作流程服務的工作流程服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)
- [從工作流程中的 Web 專案中呼叫 WCF 服務](https://go.microsoft.com/fwlink/?LinkId=207725)
