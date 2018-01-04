---
title: "屬性與。引數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1b9083ecd147a1247209b272dfd1d7b0e3c74f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="properties-vs-arguments"></a>屬性與。引數
有許多選項可用來將資料傳入活動。 除了使用 <xref:System.Activities.InArgument> 以外，您也可以使用標準 CLR 屬性或公用 <xref:System.Activities.ActivityAction> 屬性來開發接收資料的活動。 本主題將討論如何選取適當的方法類型。  
  
## <a name="using-clr-properties"></a>使用 CLR 屬性  
 將資料傳入活動時，CLR 屬性 (亦即，使用 Get 和 Set 常式來公開資料的公用方法) 是具有最多限制的選項。 編譯方案時，必須已知傳入 CLR 屬性的參數值。此值對於工作流程的每個執行個體都相同。 如此一來，傳遞到 CLR 屬性的值就會類似程式碼中定義的常數；在活動存留期內，這個值不能更改，也不能因為該活動的不同執行個體而更改。 <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> 是 CLR 屬性範例，該屬性由活動公開；該活動所呼叫的方法名稱不能隨著執行階段條件而變更，且在該活動的每個執行個體中皆相同。  
  
## <a name="using-arguments"></a>使用引數  
 如果在活動存留期內只評估資料一次，則應使用引數；也就是說，在活動存留期內，其值不會更改，但這個值在活動的不同執行個體中是可以改變的。 <xref:System.Activities.Statements.If.Condition%2A> 是只評估一次的值的範例；因此，該值會定義為引數。 <xref:System.Activities.Statements.WriteLine.Text%2A> 是另一個應定義為引數之方法的範例，因為在活動執行期間只會評估這個方法一次，但在活動的不同執行個體中可以不同。  
  
## <a name="using-activityaction"></a>使用 ActivityAction  
 當資料必須在活動執行的存留期內評估多次時，您就應該使用 <xref:System.Activities.ActivityAction>。 例如，系統會針對 <xref:System.Activities.Statements.While.Condition%2A> 迴圈的每個反覆項目評估 <xref:System.Activities.Statements.While> 屬性。 如果 <xref:System.Activities.InArgument> 已用於此目的，迴圈永遠都不會結束，因為系統不會針對每個反覆項目重新評估引數，而且一定會傳回相同的結果。
