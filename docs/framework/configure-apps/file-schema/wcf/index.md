---
title: WCF 組態結構描述
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7286793d6b2ad94c656dd37cdcc5fe1b0ab85660
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-configuration-schema"></a>WCF 組態結構描述
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 組態項目可讓您設定 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務與用戶端應用程式。 您可使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) 來建立並修改用戶端與服務的組態檔。 由於組態檔採用 XML 格式，因此，如果要使用文字編輯器手動編輯這些檔案，則必須熟悉 XML。 否則，您可能會碰到 XML 項目標記或屬性找不到等問題， 因為 XML 項目標記與屬性有區分大小寫。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 組態系統是以 <xref:System.Configuration> 命名空間為基礎。 因此，您可以使用 <xref:System.Configuration> 命名空間提供的所有標準功能，例如組態鎖定、加密與合併，以提升應用程式及其組態的安全性。 如需這些概念的詳細資訊，請參閱下列主題。  
  
 [加密組態資訊](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [鎖定組態設定](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 本節說明每個組態項目的所有可能值，以及項目如何與其他 WCF 組態項目互動。 下圖說明 WCF 組態結構描述。  
  
 ![WCF 組態結構描述](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  您應該透過適當的存取控制清單 (ACL) 保護應用程式組態檔 (app.config) 中的 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 組態區段，以防任何潛在的安全性威脅侵入。  例如，您要確定只有適當人員才能存取或修改應用程式繫結上的安全性設定，或是服務組態檔的服務模型區段。  
  
## <a name="in-this-section"></a>本節內容  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 說明 `ServiceModel` 項目。  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 設定 SMSvcHost.exe 工具。  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 使用 <xref:System.Runtime.Serialization.DataContractSerializer> 等序列化程式時，設定選項的最上層項目。  
  
## <a name="related-sections"></a>相關章節  
 [設定 Windows Communication Foundation 應用程式](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 說明如何設定 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務與用戶端。
