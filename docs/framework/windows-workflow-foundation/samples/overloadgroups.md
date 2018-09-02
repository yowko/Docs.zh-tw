---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469865"
---
# <a name="overloadgroups"></a>OverloadGroups
這個範例是由 (`CreateLocation`) 活動所組成，這個活動有兩個有趣的特性：  
  
1.  它有一些必要的引數及一些選擇性的引數。  
  
2.  它可讓使用者選擇提供兩組不同引數的其中一組。  
  
 這些行為是使用下列兩個功能所完成：  
  
-   `[isRequired]` 會驗證特定活動的屬性已指派，如果未指派則會擲回例外狀況。  
  
-   `[OverloadGroup]` 會將一組引數放在一起，好讓活動的使用者可以選擇使用某一組或另一組。 使用者不能在相同執行個體中使用不同多載群組內的引數。  
  
 在設定不同的工作流程之後，請呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，它會傳回 <xref:System.Activities.Validation.ValidationResults> 的 <xref:System.Activities.Validation.Constraint> 集合。 請將 <xref:System.Activities.Validation.Constraint> 物件列印到主控台。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  開啟**OverloadGroups.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
