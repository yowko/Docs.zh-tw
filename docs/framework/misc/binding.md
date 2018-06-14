---
title: '&lt;繫結&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: d72b3a34e0696df944b2338c89f167c8bfa06400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392248"
---
# <a name="ltbindinggt"></a>&lt;繫結&gt;
您可以使用 `binding` 項目來設定 Windows Communication Foundation (WCF) 所提供的各種預先定義繫結。  
  
## <a name="system-provided-binding"></a>系統提供的繫結  
 系統提供的繫結會隱藏 WCF 訊息堆疊的複雜性。 使用系統提供之繫結的應用程式不需要對堆疊有完整控制權。 在每個系統提供之繫結上公開的屬性，最適合繫結所處理的使用案例。  
  
 每個系統提供之繫結的組態區段可定義用於設定繫結的多個組態。 每個組態是由唯一的名稱來識別。  
  
 您無法在系統提供的繫結中加入項目或屬性。 若要這麼做，您應實作自訂繫結，如本主題的「自訂繫結」一節所述。 您可以定義完全仿照系統提供之繫結的自訂繫結，並在其中加入一些使用者應用程式要有控制權的設定。  
  
## <a name="custom-binding"></a>自訂繫結  
 自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。 個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。 每個項目都會定義及設定堆疊的一個項目。 各個自訂繫結中一定要出現一個而且是唯一一個 `transport` 項目。 如果沒有這個項目，訊息堆疊就不完整。  
  
 項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。 建議的堆疊項目順序如下所示：  
  
1.  交易 (選擇性)  
  
2.  可信賴傳訊 (選擇性)  
  
3.  安全性 (選擇性)  
  
4.  編碼器  
  
5.  Transport  
  
 自訂繫結是由其 `name` 屬性所識別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [繫結](../../../docs/framework/wcf/bindings.md)  
 [自訂繫結](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
