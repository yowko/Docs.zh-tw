---
title: 在 IIS 與 WAS 中以組態為基礎的啟動
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: d15202a7d34f3246cd7679687b6a510252fe3541
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527905"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>在 IIS 與 WAS 中以組態為基礎的啟動
通常當裝載在 Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 下的 Windows Communication Foundation (WCF) 服務，您必須提供.svc 檔案。 .svc 檔案包含服務名稱和選擇性自訂服務主機處理站。 此額外的檔案會增加管理能力的負荷。 以組態為基礎的啟動功能可免除 .svc 檔案的需求以及關聯的負荷。  
  
## <a name="configuration-based-activation"></a>以組態為基礎的啟用  
 以組態為基礎的啟動會使用放置於 .svc 檔案中的中繼資料，並將中繼資料放置於 Web.config 檔案中。 在 <`serviceHostingEnvironment`> 元素沒有 <`serviceActivations`> 項目。 在 <`serviceActivations`> 項目是否有一或多個 <`add`> 項目，一個用於每個託管服務。 <`add`> 元素包含可讓您設定服務和服務類型或服務主機處理站的相對位址的屬性。 下列組態範例程式碼會示範此區段的使用方式。  
  
> [!NOTE]
>  每個 <`add`> 項目必須指定服務或處理站屬性。 系統允許同時指定服務和處理站屬性。  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 如果 Web.config 檔案具有這項設定，您就可以將服務原始程式碼放置於應用程式的 App_Code 目錄中，或者將已編譯的組件放置於應用程式的 Bin 目錄中。  
  
> [!NOTE]
>  -   使用以組態為基礎的啟動時，不支援 .svc 檔案中的內嵌程式碼。  
> -   `relativeAddress`屬性必須設為相對位址這類 「\<子目錄 > / service.svc"或"~ /\<子 sub-directory/service.svc"。  
> -   如果您註冊未包含與 WCF 關聯之已知副檔名的相對位址，便會擲回組態例外。  
> -   指定的相對位址與虛擬應用程式的根相關。  
> -   由於組態模型為階層式，主機上註冊的相對位址和網站層級會由虛擬應用程式繼承。  
> -   在組態檔中的註冊優先權高於 .svc、.xamlx、.xoml 或其他檔案中的設定。  
> -   任何在 URI 中傳送至 IIS/WAS 的 ‘\’ (反斜線) 會自動轉換為 ‘/’ (正斜線)。 如果新增包含 ‘\’ 的相對位址且您傳送使用相對位址的 URI 至 IIS，反斜線會轉換為正斜線，而 IIS 無法將其與相對位址比對。 IIS 會送出追蹤資訊，表示找不到相符的項目。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [裝載服務](../../../../docs/framework/wcf/hosting-services.md)  
 [裝載工作流程服務概觀](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Windows Server App Fabric 主控功能](https://go.microsoft.com/fwlink/?LinkId=201276)
