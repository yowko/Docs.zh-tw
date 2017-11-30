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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
