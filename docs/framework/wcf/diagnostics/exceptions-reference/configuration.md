---
title: 組態
ms.date: 03/30/2017
ms.assetid: 86a6e12f-73b5-450e-8725-f4ca5fe0702c
ms.openlocfilehash: 3ef91a1f851f87ebf35669748f8beb1c6a880ae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="configuration"></a>組態
本主題列出 Windows Communication Foundation (WCF) 組態所產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|ConfigBindingCannotBeConfigured|無法設定服務端點上的繫結。|  
|ConfigElementKeyNull|特定組態項目金鑰不可為 null。|  
|ConfigExtensionTypeNotRegisteredInCollection|特定副檔名集合中尚未註冊特定副檔名類型。|  
|ConfigIndexOutOfRange|特定屬性值已超出範圍。|  
|ConfigInvalidBindingConfigurationName|特定組態沒有包含特定名稱的繫結。|  
|ConfigInvalidBindingName|特定組態沒有包含特定名稱的繫結。 此繫結值無效。|  
|ConfigInvalidCommonEndpointBehaviorType|無法將特定行為副檔名新增至一般端點行為，因為它尚未實作特定類型。|  
|ConfigInvalidCommonServiceBehaviorType|無法將特定行為副檔名新增至一般服務行為，因為它尚未實作特定類型。|  
|ConfigInvalidEndpointBehaviorType|無法將特定行為副檔名新增至特定端點行為，因為基礎行為類型未實作 IServiceBehavior 介面。|  
|ConfigInvalidExtensionType|特定類型必須衍生自將用於集合的特定副檔名。|  
|ConfigInvalidServiceBehaviorType|無法將行為副檔名新增至包含特定名稱的服務行為，因為基礎行為類型未實作 IServiceBehavior 介面。|  
|ConfigMessageEncodingAlreadyInBinding|無法新增特定的訊息編碼項目。 特定繫結中已經存在另一個訊息編碼項目。 每個繫結只能有一個訊息編碼項目。|  
|ConfigNoExtensionCollectionAssociatedWithType|無法找到與特定類型副檔名相關的副檔名集合。|  
|ConfigSectionNotFound|無法建立特定組態區段。 Machine.config 檔案中的資訊遺失。 請確認此組態區段已順利註冊，而且您的區段名稱拼字正確。 如果是 Windows Communication Foundation 區段，請執行 ServiceModelReg.exe -i 來修復此錯誤。|  
|ConfigTransportAlreadyInBinding|無法新增特定的傳輸項目。 另一個傳輸項目已經存在特地繫結中。 每個繫結只能有一個訊息編碼項目。|
