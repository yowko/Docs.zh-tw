---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 180e954661319cb32edfd3180418fe9b1571ea5c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>方法  
 TcpTransportBindingElement 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 TcpTransportBindingElement 類別具有下列屬性：  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 資料型別：TcpConnectionPoolSettings  
  
 存取類型：唯讀  
  
 連線集區設定。  
  
### <a name="listenbacklog"></a>ListenBacklog  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可以擱置之佇列連線要求的最大數目。  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，這個值指定是否為此連線啟用 TCP 連接埠共用。  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，指定是否啟用 Teredo (對防火牆後的用戶端進行定址的技術)。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
