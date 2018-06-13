---
title: '&lt;transactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: c708098676e5634281e29c17639304a1a9cf5afe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748707"
---
# <a name="lttransactionflowgt"></a>&lt;transactionFlow&gt;
指定自訂繫結程序的異動流程支援。  
  
 \<system.serviceModel>  
\<繫結 >  
\<customBinding>  
\<繫結 >  
\<transactionFlow >  
  
## <a name="syntax"></a>語法  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|transactionProtocol|指定要使用的交易通訊協定。 有效值包括以下的值：<br /><br /> -OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> 預設值為 OleTransactions。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 這個項目可以讓您啟用或停用端點繫結程序設定的傳入異動流程，以及指定傳入異動的所需通訊協定格式。 如需有關如何使用這個組態項目的詳細資訊，請參閱[ServiceModel 異動組態](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)和[啟用交易流程](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。  
  
> [!CAUTION]
>  當使用 `OleTransactions` 通訊協定在端點之間流動交易時，如果目的端點嘗試使用任何 `OleTransactions` 以外的通訊協定再次流動時，交易逾時可能會遺失。 這會導致 OleTransactions 躍點後的所有下層節點比預期的時間更晚發生逾時。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [ServiceModel 異動組態](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [啟用異動流程](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
