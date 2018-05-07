---
title: 端點
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint"></a>端點
端點  
  
## <a name="syntax"></a>語法  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a>方法  
 Endpoint 類別定義下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|擷取作業效能計數器執行個體名稱|  
  
## <a name="properties"></a>屬性  
 Endpoint 類別具有下列屬性：  
  
### <a name="address"></a>地址  
 資料型別：字串  
  
 存取類型：唯讀  
  
 包含端點位址的 URI。  
  
### <a name="addressheaders"></a>AddressHeaders  
 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 附加到此端點之位址標頭的集合。  
  
### <a name="addressidentity"></a>AddressIdentity  
 資料型別：字串  
  
 存取類型：唯讀  
  
 端點的身分識別。  
  
### <a name="appdomainid"></a>AppDomainId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載端點之 appdomain 的 appdomain 識別碼。  
  
### <a name="behaviors"></a>行為  
 資料型別：行為陣列  
  
 存取類型：唯讀  
  
 此端點實作之行為的集合。  
  
### <a name="binding"></a>繫結  
 資料型別：繫結  
  
 存取類型：唯讀  
  
 此端點所使用的繫結。  
  
### <a name="contractname"></a>ContractName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定公開此端點之合約的字串。  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 端點之效能計數器執行個體的名稱。  
  
### <a name="listenuri"></a>ListenUri  
 資料型別：字串  
  
 存取類型：唯讀  
  
 端點接聽的 Uri。  
  
### <a name="name"></a>名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 此端點的唯一名稱。  
  
### <a name="processid"></a>ProcessId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載端點之處理序的處理序識別碼。  
  
### <a name="ref"></a>ref  
 資料型別：合約  
  
 存取類型：唯讀  
  
 此端點公開的合約。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
