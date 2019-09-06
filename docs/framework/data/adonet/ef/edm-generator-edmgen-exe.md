---
title: EDM 產生器 (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 688989fea6037cc989267e14b103210c2a995afa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251620"
---
# <a name="edm-generator-edmgenexe"></a>EDM 產生器 (EdmGen.exe)

EdmGen.exe 是用於處理 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 模型和對應檔案的命令列工具。 您可以使用 EdmGen.exe 工具執行下列動作：

- 使用資料來源特定的 .NET Framework 資料提供者連接至資料來源，並產生 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 使用的概念模型 (.csdl)、儲存體模型 (.ssdl) 和對應 (.msl) 檔案。 如需詳細資訊，請參閱[如何：使用 Edmgen.exe 來產生模型和對應](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)檔。

- 驗證現有模型。 如需詳細資訊，請參閱[如何：使用 Edmgen.exe 來驗證模型和對應](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)檔。

- 產生 C# 或 Visual Basic 程式碼檔案，其中包含從概念模型 (.csdl) 檔案產生的物件類別 (Class)。 如需詳細資訊，請參閱[如何：使用 Edmgen.exe 來產生物件層程式碼](how-to-use-edmgen-exe-to-generate-object-layer-code.md)。

- 產生 C# 或 Visual Basic 程式碼檔案，其中包含為現有模型預先產生的檢視表。 如需詳細資訊[, 請看:預先產生視圖以改善查詢效能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))。

Edmgen.exe 工具會安裝在 .NET Framework 目錄中。 在許多情況下，這是位於 C:\windows\Microsoft.NET\Framework\v4.0。 若為 64 位元系統，則是位於 C:\windows\Microsoft.NET\Framework64\v4.0。 您也可以從 Visual Studio 命令提示字元存取 Edmgen.exe 工具 (按一下 **開始**, 指向 **所有程式**, 指向  **Microsoft Visual Studio 2010**, 指向  **Visual Studio Tools**, 然後按一下  **Visual Studio 2010命令提示**字元)。

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

|選項|說明|
|------------|-----------------|
|`/p[roject]:`\<string>|指定要使用的專案名稱。 專案名稱會當成命名空間 (Namespace) 設定的預設值、模型和對應檔案的名稱、物件來源檔案的名稱和檢視表產生來源檔案的名稱。 實體容器名稱會設定為\<project > 內容。|
|`/prov[ider]:`\<string>|要用來產生儲存體模型 (.ssdl) 檔案的 .NET Framework 資料提供者名稱。 預設提供者為 .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>)。|
|`/c[onnectionstring]:`\<連接字串 >|指定用來連接至資料來源的字串。|
|`/incsdl:`\<file>|指定 .csdl 檔案或 .csdl 檔案所在的目錄。 這個引數可多次指定，因此您能指定數個目錄或 .csdl 檔案。 當概念模型被分割成數個檔案後，指定多個目錄會有助於產生類別 (`/mode:EntityClassGeneration`) 或檢視表 (`/mode:ViewGeneration`)， 而這也有助於驗證多個模型 (`/mode:ValidateArtifacts`)。|
|`/refcsdl:`\<file>|指定用於解析來源 .csdl 檔案中任何參考的其他 .csdl 檔案 (來源 .csdl 檔案是由 `/incsdl` 選項所指定的檔案)。 `/refcsdl` 檔案包含來源 .csdl 檔案相依的類型。 這個引數可多次指定。|
|`/inmsl:`\<file>|指定 .msl 檔案或 .msl 檔案所在的目錄。 這個引數可多次指定，因此您能指定數個目錄或 .msl 檔案。 當概念模型被分割成數個檔案後，指定多個目錄會有助於產生檢視表 (`/mode:ViewGeneration`)， 而這也有助於驗證多個模型 (`/mode:ValidateArtifacts`)。|
|`/inssdl:`\<file>|指定 .ssdl 檔案或 .ssdl 檔案所在的目錄。 這個引數可多次指定，因此您能指定數個目錄或 .ssdl 檔案。 這有助於驗證多個模型 (`(/mode:ValidateArtifacts)`)。|
|`/outcsdl:`\<file>|指定將建立的 .csdl 檔案名稱。|
|`/outmsl:`\<file>|指定將建立的 .msl 檔案名稱。|
|`/outssdl:`\<file>|指定將建立的 .ssdl 檔案名稱。|
|`/outobjectlayer:`\<file>|指定原始程式碼檔案，其中包含從 .csdl 檔案產生的物件。|
|`/outviews:`\<file>|指定原始程式碼檔案，其中包含已產生的檢視表。|
|`/language:`[VB&#124;CSharp]|指定所產生之原始程式碼檔案的語言。 預設語言為 C#。|
|`/namespace:`\<string>|指定要使用的模型命名空間。 執行 `/mode:FullGeneration` 或 `/mode:FromSSDLGeneration` 時會在 .csdl 檔案中設定命名空間。 執行 `/mode:EntityClassGeneration` 時不會使用命名空間。|
|`/entitycontainer:`\<string>|指定要套用到產生的模型和對應檔案中 `<EntityContainer>` 項目的名稱。|
|`/pl[uralize]`|將英語的單數和複數規則套用到概念模型中的 `Entity`、`EntitySet` 和 `NavigationProperty` 名稱。 這個選項會執行下列動作：<br /><br /> -將所有`EntityType`名稱單數。<br />-將所有`EntitySet`名稱設為複數。<br />-對於最`NavigationProperty`多隻傳回一個實體的每個, 請將名稱變成單數。<br />-若每`NavigationProperty`個傳回一個以上的實體, 請將名稱設為複數。|
|`/SuppressForeignKeyProperties or /nofk`|防止外部索引鍵資料行公開為概念模型中實體類型上的純量屬性。|
|`/help` 或 `?`|顯示工具的命令語法和選項。|
|`/nologo`|隱藏著作權訊息。|
|`/targetversion:`\<字串 >|用於編譯產生的程式碼的 .NET Framework 版本。 支援的版本為 4 和 4.5。 預設為 4。|

## <a name="in-this-section"></a>本節內容

[如何：使用 Edmgen.exe 來產生模型和對應檔](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[如何：使用 Edmgen.exe 來產生物件層程式碼](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[如何：使用 Edmgen.exe 來驗證模型和對應檔](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>另請參閱

- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [實體資料模型](../entity-data-model.md)
- [CSDL、SSDL 和 MSL 規格](./language-reference/csdl-ssdl-and-msl-specifications.md)
