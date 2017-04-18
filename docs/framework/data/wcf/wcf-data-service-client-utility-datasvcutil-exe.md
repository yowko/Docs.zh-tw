---
title: "WCF Data Services 用戶端公用程式 (DataSvcUtil.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 用戶端程式庫"
  - "WCF Data Services, 使用"
  - "WCF Data Services, 產生用戶端資料類別"
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# WCF Data Services 用戶端公用程式 (DataSvcUtil.exe)
DataSvcUtil.exe 是 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 提供的命令列工具，它會取用 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要，並產生從 .NET Framework 用戶端應用程式存取資料服務所需的用戶端資料服務類別。  此公用程式可以透過使用下列中繼資料來源產生資料類別：  
  
-   資料服務的根 URI。  此公用程式會要求服務中繼資料文件，以描述資料服務所公開的資料模型。  如需詳細資訊，請參閱 [OData：服務中繼資料文件](http://go.microsoft.com/fwlink/?LinkId=186070)。  
  
-   使用概念結構定義語言 \(CSDL\) 定義的資料模型檔案 \(.csdl\)，如同 [\[MC\-CSDL\]：概念結構定義檔案格式](http://go.microsoft.com/fwlink/?LinkID=159072)規格中所定義。  
  
-   使用 Entity Framework 提供之實體資料模型所建立的 .edmx 檔案。  如需詳細資訊，請參閱 [\[MC\-EDMX\]：資料服務封裝格式的實體資料模型](http://go.microsoft.com/fwlink/?LinkID=178833)規格。  
  
 如需詳細資訊，請參閱[HOW TO：手動產生用戶端資料服務類別](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。  
  
 DataSvcUtil.exe 工具安裝在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 目錄中。  在許多情況下，這會位於 C:\\Windows\\Microsoft.NET\\Framework\\v4.0。  若為 64 位元系統，則是位於 C:\\Windows\\Microsoft.NET\\Framework64\\v4.0。  您也可以從 Visual Studio 命令提示字元 \(按一下 \[**開始**\]，指向 \[**所有程式**\]、指向 \[**Microsoft Visual Studio 2010**\]、指向 \[**Visual Studio Tools**\]，然後按一下 \[**Visual Studio 2010 命令提示字元**\]\)，存取 DataSvcUtil.exe 工具。  
  
## 語法  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### 參數  
  
|選項|描述|  
|--------|--------|  
|`/dataservicecollection`|指定同時產生將物件繫結至控制項所需的程式碼。|  
|`/help`<br /><br /> \-或\-<br /><br /> `/?`|顯示工具的命令語法和選項。|  
|`/in:` *\<file\>*|指定 .csdl 或 .edmx 檔案，或是檔案所在的目錄。|  
|`/language:`\[VB&#124;CSharp\]|指定所產生之原始程式碼檔案的語言。  預設語言為 C\#。|  
|`/nologo`|隱藏著作權訊息。|  
|`/out:` *\<file\>*|指定原始程式碼檔案的名稱，該檔案包含已產生的用戶端資料服務類別。|  
|`/uri:` *\<string\>*|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的 URI。|  
|`/version:`\[1.0&#124;2.0\]|指定 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 的最高接受版本。  版本是根據 DataService 元素的 `DataServiceVersion` 屬性而決定，此元素包含在所傳回的資料服務中繼資料中。  如需詳細資訊，請參閱[資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。  當您指定 `/dataservicecollection` 參數時，必須一併指定 `/version:2.0`，以啟用資料繫結。|  
  
## 請參閱  
 [產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)   
 [HOW TO：加入資料服務參考](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)