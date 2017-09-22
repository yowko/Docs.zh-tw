---
title: "如何：設定應用程式定義域"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4f8c91a11deac63e2ad44628a609ed4ca6501e84
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：設定應用程式定義域
您可以使用 <xref:System.AppDomainSetup> 類別提供 Common Language Runtime 新的應用程式定義域組態資訊。  建立自己的應用程式定義域時，最重要的屬性就是 <xref:System.AppDomainSetup.ApplicationBase%2A>。  其他 **AppDomainSetup** 屬性主要是由執行階段主應用程式用來組態特定的應用程式定義域。  
  
 **ApplicationBase** 屬性定義應用程式的根目錄。  當執行階段必須滿足型別要求時，它必須在 **ApplicationBase** 屬性指定的目錄中檢查含有該型別的組件。  
  
> [!NOTE]
>  新的應用程式定義域只會繼承建立者的 **ApplicationBase** 屬性。  
  
 下列範例建立 **AppDomainSetup** 類別的執行個體 \(Instance\)、使用該類別建立新的應用程式定義域、撰寫資訊到主控台，然後卸載應用程式定義域。  
  
## 範例  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [使用應用程式定義域設計程式](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)

