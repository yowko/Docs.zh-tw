---
title: Channel 類別
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="channel-class"></a>Channel 類別
通道  
  
## <a name="syntax"></a>語法  
  
```  
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
 資料型別：字串  
  
 存取類型：唯讀  
  
 通道的本機端點。  
  
### <a name="ref"></a>ref  
 資料型別：端點  
  
 存取類型：唯讀  
  
 通道所連接之端點的參考。  
  
### <a name="remoteaddress"></a>RemoteAddress  
 資料型別：字串  
  
 存取類型：唯讀  
  
 與通道相關聯的遠端位址。  
  
### <a name="sessionid"></a>SessionId  
 資料型別：字串  
  
 存取類型：唯讀  
  
 目前工作階段識別碼 (如果有)。  
  
### <a name="type"></a>類型  
 資料型別：字串  
  
 存取類型：唯讀  
  
 通道的類型。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.ChannelBase>
