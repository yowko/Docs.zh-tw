---
title: "EDM 產生器 (EdmGen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ee356fc3e7d6e1279e0cba8014d6d285620add3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="edm-generator-edmgenexe"></a>EDM 產生器 (EdmGen.exe)
EdmGen.exe 是用於處理 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 模型和對應檔案的命令列工具。 您可以使用 EdmGen.exe 工具執行下列動作：  
  
-   使用資料來源特定的 .NET Framework 資料提供者連接至資料來源，並產生 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 使用的概念模型 (.csdl)、儲存體模型 (.ssdl) 和對應 (.msl) 檔案。 如需詳細資訊，請參閱[How to： 使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
-   驗證現有模型。 如需詳細資訊，請參閱[How to： 使用 EdmGen.exe 驗證模型和對應檔案](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)。  
  
-   產生 C# 或 Visual Basic 程式碼檔案，其中包含從概念模型 (.csdl) 檔案產生的物件類別 (Class)。 如需詳細資訊，請參閱[How to： 使用 EdmGen.exe 產生物件層程式碼](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)。  
  
-   產生 C# 或 Visual Basic 程式碼檔案，其中包含為現有模型預先產生的檢視表。 如需詳細資訊， [How to: Pre-Generate 檢視，以改善查詢效能](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)。  
  
 EdmGen.exe 工具是安裝在 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 目錄。 在許多情況下，這是位於 C:\windows\Microsoft.NET\Framework\v4.0。 若為 64 位元系統，則是位於 C:\windows\Microsoft.NET\Framework64\v4.0。 您也可以從 Visual Studio 命令提示字元存取 EdmGen.exe 工具 (按一下**啟動**，指向 **所有程式**，指向  **Microsoft Visual Studio 2010**，指向**Visual Studio Tools**，然後按一下  **Visual Studio 2010 命令提示字元**)。  
  
## <a name="syntax"></a>語法  
  
```  
EdmGen /mode:choice [options]  
```  
  
## <a name="mode"></a>模式  
 使用 EdmGen.exe 工具時，必須指定下列其中一個模式。  
  
|模式|描述|  
|----------|-----------------|  
|`/mode:ValidateArtifacts`|驗證 .csdl、.ssdl 和 .msl 檔案，並顯示任何錯誤或警告。<br /><br /> 這個選項至少需要 `/inssdl`、`/incsdl` 兩個引數其中之一。 如果指定 `/inmsl`，則也要有 `/inssdl` 和 `/incsdl` 引數。|  
|`/mode:FullGeneration`|使用 `/connectionstring` 選項中指定的資料庫連接資訊，並產生 .csdl、.ssdl、.msl、物件層和檢視表檔案。<br /><br /> 這個選項需要 `/connectionstring` 引數以及 `/project` 引數或是 `/outssdl`、`/outcsdl`、`/outmsdl`、`/outobjectlayer`、`/outviews`、`/namespace` 及 `/entitycontainer` 其中一個引數。|  
|`/mode:FromSSDLGeneration`|從指定的 .ssdl 檔案產生 .csdl 與 .msl 檔案、原始程式碼和檢視表。<br /><br /> 這個選項需要 `/inssdl` 引數及 `/project` 引數或 `/outcsdl`、`/outmsl`、`/outobjectlayer`、`/outviews`、`/namespace,` 和 `/entitycontainer` 引數。|  
|`/mode:EntityClassGeneration`|建立原始程式碼檔案，其中包含從 .csdl 檔案產生的類別。<br /><br /> 這個選項需要 `/incsdl` 引數及 `/project` 引數或 `/outobjectlayer` 引數。 `/language` 引數是選擇性的。|  
|`/mode:ViewGeneration`|建立原始程式碼檔案，其中包含從 .csdl、.ssdl 和 .msl 檔案產生的檢視表。<br /><br /> 這個選項需要 `/inssdl`、`/incsdl`、`/inmsl,` 及 `/project` 或 `/outviews` 引數。 `/language` 引數是選擇性的。|  
  
## <a name="options"></a>選項  
  
|選項|描述|  
|------------|-----------------|  
|`/p[roject]:`\<字串 >|指定要使用的專案名稱。 專案名稱會當成命名空間 (Namespace) 設定的預設值、模型和對應檔案的名稱、物件來源檔案的名稱和檢視表產生來源檔案的名稱。 實體容器名稱設\<專案 > 內容。|  
|`/prov[ider]:`\<字串 >|要用來產生儲存模型 (.ssdl) 檔案的 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 資料提供者的名稱。 預設提供者是[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>)。|  
|`/c[onnectionstring]:`\<連接字串 >|指定用來連接至資料來源的字串。|  
|`/incsdl:`\<檔案 >|指定 .csdl 檔案或 .csdl 檔案所在的目錄。 這個引數可多次指定，因此您能指定數個目錄或 .csdl 檔案。 當概念模型被分割成數個檔案後，指定多個目錄會有助於產生類別 (`/mode:EntityClassGeneration`) 或檢視表 (`/mode:ViewGeneration`)， 而這也有助於驗證多個模型 (`/mode:ValidateArtifacts`)。|  
|`/refcsdl:`\<檔案 >|指定用於解析來源 .csdl 檔案中任何參考的其他 .csdl 檔案  (來源 .csdl 檔案是由 `/incsdl` 選項所指定的檔案)。 `/refcsdl` 檔案包含來源 .csdl 檔案相依的類型。 這個引數可多次指定。|  
|`/inmsl:`\<檔案 >|指定 .msl 檔案或 .msl 檔案所在的目錄。 這個引數可多次指定，因此您能指定數個目錄或 .msl 檔案。 當概念模型被分割成數個檔案後，指定多個目錄會有助於產生檢視表 (`/mode:ViewGeneration`)， 而這也有助於驗證多個模型 (`/mode:ValidateArtifacts`)。|  
|`/inssdl:`\<檔案 >|指定 .ssdl 檔案或 .ssdl 檔案所在的目錄。 這個引數可多次指定，因此您能指定數個目錄或 .ssdl 檔案。 這有助於驗證多個模型 (`(/mode:ValidateArtifacts)`)。|  
|`/outcsdl:`\<檔案 >|指定將建立的 .csdl 檔案名稱。|  
|`/outmsl:`\<檔案 >|指定將建立的 .msl 檔案名稱。|  
|`/outssdl:`\<檔案 >|指定將建立的 .ssdl 檔案名稱。|  
|`/outobjectlayer:`\<檔案 >|指定原始程式碼檔案，其中包含從 .csdl 檔案產生的物件。|  
|`/outviews:`\<檔案 >|指定原始程式碼檔案，其中包含已產生的檢視表。|  
|`/language:`[VB &#124;CSharp]|指定所產生之原始程式碼檔案的語言。 預設語言為 C#。|  
|`/namespace:`\<字串 >|指定要使用的模型命名空間。 執行 `/mode:FullGeneration` 或 `/mode:FromSSDLGeneration` 時會在 .csdl 檔案中設定命名空間。 執行 `/mode:EntityClassGeneration` 時不會使用命名空間。|  
|`/entitycontainer:`\<字串 >|指定要套用到產生的模型和對應檔案中 `<EntityContainer>` 項目的名稱。|  
|`/pl[uralize]`|將英語的單數和複數規則套用到概念模型中的 `Entity`、`EntitySet` 和 `NavigationProperty` 名稱。 這個選項會執行下列動作：<br /><br /> -請所有`EntityType`單數名稱。<br />-請所有`EntitySet`複數名稱。<br />-針對每個`NavigationProperty`，傳回最多一個實體，讓名稱成為唯一。<br />-針對每個`NavigationProperty`傳回多個實體，讓名稱成為複數。|  
|`/SupressForeignKeyProperties or /nofk`|防止外部索引鍵資料行公開為概念模型中實體類型上的純量屬性。|  
|`/help` 或 `?`|顯示工具的命令語法和選項。|  
|`/nologo`|隱藏著作權訊息。|  
|`/targetversion:`\<字串 >|用於編譯產生的程式碼的 .NET Framework 版本。 支援的版本為 4 和 4.5。 預設為 4。|  
  
## <a name="in-this-section"></a>本節內容  
 [如何：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
 [如何：使用 EdmGen.exe 產生物件層程式碼](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)  
  
 [如何：使用 EdmGen.exe 驗證模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)  
  
## <a name="see-also"></a>請參閱  
 [ADO.NET 實體資料模型工具](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [實體資料模型](../../../../../docs/framework/data/adonet/entity-data-model.md)  
 [CSDL、SSDL 和 MSL 規格](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
