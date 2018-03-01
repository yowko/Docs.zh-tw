---
title: "Windows Communication Foundation 繫結概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bc4fc7559872a808c2de87e4926075614351030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-bindings-overview"></a>Windows Communication Foundation 繫結概觀
繫結是一種物件，可用來指定連線至 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務端點時所需的通訊詳細資料。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務中的每個端點都需要繫結才能正確地指定。 這個主題會概述繫結所定義的通訊詳細資料類型、繫結項目、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中所含的繫結以及對端點指定繫結的方式。  
  
## <a name="what-a-binding-defines"></a>繫結所定義的內容  
 繫結中的資訊可能很基本，也可能很複雜。 最基本的繫結只會指定連線至端點時必須使用的傳輸通訊協定 (例如 HTTP)。 更一般來說，繫結中所含與如何連線至端點有關的資訊，與下列其中一種類別息息相關。  
  
 通訊協定  
 判斷使用的安全性機制：可靠的傳訊能力或交易內容流量設定。  
  
 編碼  
 判斷訊息的編碼方式 (例如，文字或二進位)。  
  
 Transport  
 判斷要使用的基礎傳輸通訊協定 (例如，TCP 或 HTTP)。  
  
## <a name="the-elements-of-a-binding"></a>繫結項目  
 繫結基本上是由排列順序的繫結項目堆疊所組成，而每個繫結項目都會指定連線至服務端點時所需的部分通訊資訊。 堆疊中最低的那兩層為必要項。 堆疊基底是傳輸繫結項目，而這個項目的正上方是其中含有訊息編碼規格的項目。 指定其他通訊協定的選用繫結元素則會置於這兩個必要元素之上。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]這些繫結項目和其正確順序，請參閱[自訂繫結](../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="system-provided-bindings"></a>系統提供的繫結  
 繫結中的資訊可能很複雜，而有些設定也可能彼此不相容。 因此，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 包含了一組系統提供的繫結。 這些繫結設計為滿足大多數應用程式需求。 下列類別則表示系統提供之繫結的一些範例：  
  
-   <xref:System.ServiceModel.BasicHttpBinding>：一種 HTTP 通訊協定繫結，可用於連線至 Web 服務，並符合 WS-I Basic Profile 規格 (例如，以 ASP.NET Web 服務為基礎的服務)。  
  
-   <xref:System.ServiceModel.WSHttpBinding>：一種互通的繫結，可用於連線至符合 WS-* 通訊協定的端點。  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>：使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 以連線至同一部電腦上的其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 端點。  
  
-   <xref:System.ServiceModel.NetMsmqBinding>：使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 以建立與其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 端點的佇列訊息連線。  
  
 如需完整清單，與所有的描述[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-提供的繫結，請參閱[之繫結](../../../docs/framework/wcf/system-provided-bindings.md)。  
  
## <a name="using-your-own-bindings"></a>使用您自己的繫結  
 如果所含之系統提供的繫結都沒有服務應用程式需要的正確功能組合，您可以建立自己的繫結。 執行這項作業的方法有兩種。 您可以使用 <xref:System.ServiceModel.Channels.CustomBinding> 物件從已存在的繫結元素中建立新的繫結，或者藉由從 <xref:System.ServiceModel.Channels.Binding> 繫結衍生，而建立完整的使用者定義繫結。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]建立您自己的繫結使用這兩種方法，請參閱[自訂繫結](../../../docs/framework/wcf/extending/custom-bindings.md)和[Creating User-Defined 繫結](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。  
  
## <a name="using-bindings"></a>使用繫結  
 使用繫結牽涉到兩個基本步驟：  
  
1.  選取或定義繫結。 最簡單的方法是選擇 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中所含的其中一個系統提供的繫結，並使用其預設值。 也可以選擇系統提供的繫結，並重設其屬性值以符合您的需求。 此外，您可以建立自訂繫結或使用者定義的繫結，以對這些繫結擁有更高程度的控制權和自訂權。  
  
2.  建立使用已選取或已定義之繫結的端點。  
  
## <a name="code-and-configuration"></a>程式碼和組態  
 有兩種方法可讓您定義繫結：透過程示碼或透過組態。 這兩個方法與您是使用系統提供的繫結或自訂繫結無關。 一般來說，使用程式碼可讓您在設計階段時完全控制繫結的定義。 相反地，使用組態則可讓 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務或用戶端的系統管理員或使用者變更繫結的參數，而不需要重新編譯服務應用程式。 使用者通常需要這種彈性，因為對於即將部署的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式來說，是沒有辦法預測特定的電腦需求。 將繫結 (和位址) 資訊留在程式碼外面，可在不需要重新編譯或重新部署應用程式的情況下，就可以變更繫結和位址資訊。 請注意，會先建立在組態中指定繫結，之後才建立在程式碼中定義的繫結，這樣可讓程式碼定義的繫結覆寫任何組態定義的繫結。  
  
## <a name="see-also"></a>請參閱  
 [使用繫結設定服務與用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
