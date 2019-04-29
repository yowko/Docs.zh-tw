---
title: WS-MetadataExchange 繫結
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795469"
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange 繫結
本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。  
  
## <a name="the-default-bindings"></a>預設繫結  
  
|預設繫結名稱|繫結的建構方式|  
|--------------------------|------------------------------------|  
|mexHttpBinding|已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|mexHttpsBinding|支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|mexNamedPipeBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>的 。|  
|mexTcpBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding> 的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。|
