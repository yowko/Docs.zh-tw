---
title: WF 中的錯誤處理活動
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707673"
---
# <a name="error-handling-activities-in-wf"></a>WF 中的錯誤處理活動
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 提供數種系統提供的活動，可用於實作錯誤處理與復原。 如需詳細資訊，請參閱 [例外狀況](exceptions.md)中定義的介面的私用 C++ 專屬實作。  
  
## <a name="error-handling-activities"></a>錯誤處理活動  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|重新擲回從 `TryCatch` 活動中上次擲回的例外狀況。|  
|<xref:System.Activities.Statements.Throw>|擲回例外狀況。|  
|<xref:System.Activities.Statements.TryCatch>|實作例外狀況處理。|
