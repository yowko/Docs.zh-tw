---
title: "Windows Communcation Foundation 繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 494869985f14dc9562b8d98a7d68cd9639cca97b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="windows-communcation-foundation-bindings"></a>Windows Communcation Foundation 繫結
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會區分應用程式的軟體撰寫方式，以及與其他軟體的通訊方式。 繫結可用來指定必要的傳輸、編碼與通訊協定詳細資料，以供用戶端與服務彼此通訊。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用繫結來產生端點的基礎 Wire 表示，因此大部分的繫結詳細資料必須由參與通訊的各方同意才行。 要達到這個目的之最簡單方式，就是讓服務用戶端使用服務端點所使用的相同繫結。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何執行這項操作，請參閱[使用繫結來設定 Windows Communication Foundation 服務和用戶端](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)。  
  
 繫結是由繫結項目集合所組成。 每個項目負責針對端點與用戶端通訊的方式稍加描述。 繫結程序必須包含至少一個傳輸繫結程序項目、一個訊息編碼繫結程序項目 (根據預設，可由傳輸繫結程序項目來提供)，以及任意數量的其他通訊協定繫結程序項目。 由此描述來建立執行階段的處理序，可讓每個繫結項目將程式碼撰寫到該執行階段中。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供的繫結包含一般的繫結項目選擇。 您可以搭配預設設定來使用它們，或是根據使用者需求來修改這些預設值。 這些系統提供的繫結所包含的屬性可讓您直接控制繫結項目與其設定。 您也可以輕鬆地同時使用多個版本的繫結，只需為每個繫結版本提供屬於自己的名稱即可。 如需詳細資訊，請參閱[Configuring System-Provided 繫結](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)。  
  
 如果您需要繫結項目的集合 (尚未由這些系統提供繫結之任意繫結所提供)，可以建立包含所需繫結項目集合的自訂繫結。 這些自訂繫結很容易建立，而且不需要新的類別，但是它們無法提供屬性讓您控制繫結項目或其設定。 您可以存取繫結項目並透過包含這些繫結項目的集合來修改其設定。 如需詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [設定系統提供的繫結](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 說明如何使用與修改 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供來支援一般案例的繫結。  
  
 [使用繫結來設定 Windows Communication Foundation 服務和用戶端](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 說明如何使用命令式程式碼以及宣告式組態來定義服務與用戶端的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 繫結。  
  
 [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 說明何謂 <xref:System.ServiceModel.Channels.CustomBinding> 與其使用時機。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>相關章節  
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)
