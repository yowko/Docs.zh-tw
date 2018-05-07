---
title: WS-MetadataExchange 繫結
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange 繫結
本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。  
  
## <a name="the-default-bindings"></a>預設繫結  
  
|預設繫結名稱|繫結的建構方式|  
|--------------------------|------------------------------------|  
|MexHttpBinding|已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|MexHttpsBinding|支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|MexNamedPipeBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>的 。|  
|MexTcpBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding> 的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。|
