---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 193000acf2f3c8a0eddb2552559ee40a0f5fced9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>方法  
 PeerTransportBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 PeerTransportBindingElement 類別具有下列屬性：  
  
### <a name="listenipaddress"></a>ListenIPAddress  
 資料型別：字串  
  
 存取類型：唯讀  
  
 對等節點接聽 TCP 訊息的 IP 位址。  
  
### <a name="port"></a>通訊埠  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 這個繫結處理對等通道 TCP 訊息所在的網路介面連接埠。  
  
### <a name="security"></a>安全性  
 資料型別：PeerSecuritySettings  
  
 存取類型：唯讀  
  
 對應傳輸安全性設定。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
