---
title: Channel 類別
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: a920636e7df9609b12834366b1488c80122f9fca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274227"
---
# <a name="channel-class"></a>Channel 類別

通路  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>方法  

 Channel 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  

 Channel 類別具有下列屬性。  
  
### <a name="localaddress"></a>LocalAddress  

 資料類型：字串  
  
 存取類型：唯讀  
  
 通道的本機端點。  
  
### <a name="ref"></a>ref  

 資料型別：端點  
  
 存取類型：唯讀  
  
 通道所連接之端點的參考。  
  
### <a name="remoteaddress"></a>RemoteAddress  

 資料類型：字串  
  
 存取類型：唯讀  
  
 與通道相關聯的遠端位址。  
  
### <a name="sessionid"></a>SessionId  

 資料類型：字串  
  
 存取類型：唯讀  
  
 目前工作階段識別碼 (如果有)。  
  
### <a name="type"></a>類型  

 資料類型：字串  
  
 存取類型：唯讀  
  
 通道的類型。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.ChannelBase>
