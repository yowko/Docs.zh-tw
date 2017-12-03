---
title: "HOW TO：使用 Svcutil.exe 來驗證已編譯服務程式碼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9aeeccc42d5fbbed34ffedf01712b208c98ec58e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>HOW TO：使用 Svcutil.exe 來驗證已編譯服務程式碼
您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來偵測服務實作和組態中的錯誤，而不需要裝載服務。  
  
### <a name="to-validate-a-service"></a>若要驗證服務  
  
1.  將服務編譯為可執行檔以及一或多個相依組件。  
  
2.  開啟 SDK 命令提示字元  
  
3.  在命令提示字元中，使用下列格式啟動 Svcutil.exe 工具。 如需有關各種不同的參數的詳細資訊，請參閱的服務 Validationsection [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)主題。  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     您必須使用 `/serviceName` 選項以指出您要驗證的服務組態名稱。  
  
     `assemblyPath` 引數會指定服務的可執行檔和一或多個組件的路徑，而這些組件中含有要驗證的服務類型。 可執行組件必須具有相關聯的組態檔，才能提供服務組態。 您可以使用標準命令列萬用字元來提供多個組件。  
  
## <a name="example"></a>範例  
 下列命令會執行在 myServiceHost.exe 可執行檔中實作的服務 myServiceName。  將會自動載入服務的組態檔 (myServiceHost.exe.config)。  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>另請參閱  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
