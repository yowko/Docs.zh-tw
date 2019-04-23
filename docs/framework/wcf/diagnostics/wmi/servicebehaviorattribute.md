---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: b6221e93f10b87a368bd594932a8c36ae14df8f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772819"
---
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>語法  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceBehaviorAttribute 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceBehaviorAttribute 類別具有下列屬性：  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否要在用戶端關閉輸出工作階段時自動關閉工作階段。  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 資料型別：字串  
存取類型：唯讀  
  
 代表服務支援單一執行緒、多重執行緒或可重新進入 (Reentrant) 呼叫。  
  
### <a name="configurationname"></a>ConfigurationName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務組態的名稱。  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否要將未知的序列化資料傳送到網路上的值。  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否要針對偵錯用途，在傳回給用戶端的 SOAP 錯誤詳細資料中包含 Managed 例外狀況資訊。  
  
### <a name="instancecontextmode"></a>InstanceContextMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定何時建立新的服務物件。  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 已序列化物件中允許的項目數目上限。  
  
### <a name="name"></a>名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 WSDL 格式的服務名稱屬性。  
  
### <a name="namespace"></a>命名空間  
 資料型別：字串  
  
 存取類型：唯讀  
  
 WSDL 格式的服務目標命名空間。  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否會在目前的異動完成時回收服務物件。  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定當目前的工作階段關閉時，是否會完成暫止的異動。  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定異動隔離等級。  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 異動必須完成的期間。  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否使用目前的同步化內容來選擇執行緒執行。  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定系統或應用程式是否會強制執行 SOAP MustUnderstand 標頭處理。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
