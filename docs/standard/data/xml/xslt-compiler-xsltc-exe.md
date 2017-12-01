---
title: "XSLT 編譯器 (xsltc.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b4ede7bdb8dad65e9cd959dfaa2f8956a877762
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT 編譯器 (xsltc.exe)
XSLT 編譯器 (xsltc.exe) 會編譯 XSLT 樣式表並產生組件。 然後編譯的樣式表可以直接傳遞到新的 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 方法中。 您無法使用 xsltc.exe 產生簽署的組件。  
  
 xsltc.exe 工具隨附於 Visual Studio 2008 中。 如需詳細資訊，請參閱[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=89463)。  
  
## <a name="syntax"></a>語法  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>引數  
  
|引數|描述|  
|--------------|-----------------|  
|`sourceFile`|指定樣式表的名稱。 樣式表必須是本機檔案或位於內部網路上。|  
  
## <a name="options"></a>選項  
  
|選項|說明|  
|------------|-----------------|  
|`/c[lass]:` `name`|為下列樣式表的類別指定名稱。 類別名稱可以是完整名稱。<br /><br /> 類別名稱預設為樣式表的名稱。 例如，如果編譯了樣式表 customers.xsl，預設類別名稱就是 customers。|  
|`/debug[`+&#124;-`]`|指定是否要產生偵錯資訊。<br /><br /> 指定 `+` 或 `/debug` 會讓編譯器產生偵錯資訊，並將其放在程式資料庫 (PDB) 檔案中。 產生的 PDB 檔案名稱是 `assemblyName`.pdb。<br /><br /> 指定 `-` (當您未指定 `/debug` 時，它就會生效) 不會建立任何偵錯資訊。 產生正式版本組件。 **注意：**偵錯模式中的編譯會大幅影響 XSLT 效能。|  
|`/help`|顯示工具的命令語法和選項。|  
|`/nologo`|隱藏編譯器著作權訊息，使其無法顯示。|  
|`/platform:` `string`|指定可執行組件的平台。 以下將描述有效的平台值：<br /><br /> `x86` 會編譯將由 32 位元、x86 相容的 Common Language Runtime 所執行的組件。<br /><br /> `x64` 會在支援 AMD64 或 EM64T 指令集的電腦上編譯將由 64 位元 Common Language Runtime 所執行的組件。<br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]組件編譯為 64 位元 common language runtime 所執行的電腦上[!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]處理器。<br /><br /> `anycpu` 會編譯要在任何平台上執行的組件。 這是預設值。|  
|`/out:` `assemblyName`|指定當做輸出的組件名稱。 組件名稱預設為主要樣式表的名稱，如果有多個樣式表存在，則預設為第一個樣式表名稱。<br /><br /> 如果此樣式表包含指令碼，指令碼會儲存到個別組件中。 指令碼組件名稱是從主要組件名稱產生而來。 例如，如果您指定 CustOrders.dll 當做組件名稱，第一個指令碼組件會命名為 CustOrders_Script1.dll。|  
|`/settings:` `document+-, script+-, DTD+-,`|指定樣式表中是否允許 `document()` 函式、XSLT 指令碼或文件類型定義 (DTD)。<br /><br /> 預設行為會停用 DTD、`document()` 函式和指令碼的支援。|  
|`@` `file`|讓您指定包含編譯器選項的檔案。|  
|`?`|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 XSLT 方案可由多個樣式表模組所組成。 xsltc.exe 工具會從樣式表產生組件。 然後此組件可以傳遞到 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 方法中。 如此將有助於在某些 XSLT 部署案例中減少效能成本。  
  
> [!NOTE]
>  您也必須將編譯的組件當做參考併入應用程式中。  
  
 Xsltc.exe 工具不會驗證類別 (`/class:``name`) 或組件 (`/out:``assemblyName`) 名稱。 如果這些名稱無效，Common Language Runtime 會擲回錯誤。  
  
## <a name="examples"></a>範例  
 下列命令會編譯樣式表，並建立名為 booksort.dll 的組件。  
  
```  
xsltc booksort.xsl  
```  
  
 下列命令會編譯樣式表，並建立名稱分別為 booksort.dll 和 booksort.pdb 的組件和 PDB 檔案。  
  
```  
xsltc booksort.xsl /debug  
```  
  
 下列命令會編譯包含 msxsl:script 項目的樣式表，並建立兩個名為 calc.dll 和 calc_Script1.dll 的組件。  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 下列命令會啟用 DTD 處理和指令碼支援，並建立兩個名為 myTest.dll 和 myTest_Script1.dll 的組件。  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 下列命令會編譯兩個樣式表模組，並建立名為 booksort.dll 的單一組件。  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [如何： 使用組件執行 XSLT 轉換](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)
