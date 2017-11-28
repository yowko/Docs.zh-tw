---
title: ".NET Framework 類別庫概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], JScript
- System namespace
- JScript, data types
- .NET Framework, class library
- type system [.NET Framework]
- data types [.NET Framework]
- value types
- data types [.NET Framework], Visual Basic
- Common Language Specification
- namespaces [.NET Framework]
- floating point value type
- class library [.NET Framework]
- CLS
- logical value type
- .NET Framework class library, about
- built-in types
- namespaces [.NET Framework], about namespaces
- Visual C++, data types
- members [.NET Framework], type
- data types [.NET Framework], C#
- integer value type
- base types, class library
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 05af1b2a881cabb418adcaaee44a819ae323e62a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="net-framework-class-library-overview"></a>.NET Framework 類別庫概觀
[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 包括類別、介面和實值型別，以加速和最佳化開發過程並提供對系統功能的存取。 為了促進語言之間的互通性 (Interoperability)，大部分 .NET Framework 型別符合 CLS 標準，因而可以用於所有符合 Common Language Specification (CLS) 程式語言編譯器之中。  
  
 .NET Framework 型別是建置 .NET 應用程式、元件和控制項的基礎。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 包含執行下列函式的型別：  
  
-   代表基底資料型別和例外狀況  
  
-   封裝資料結構  
  
-   執行 I/O  
  
-   存取有關已載入型別的資訊  
  
-   叫用 .NET Framework 安全性檢查  
  
-   提供資料存取、豐富型用戶端 (Rich Client) GUI 和伺服器控制的用戶端 GUI  
  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 提供相當豐富的介面，以及抽象和具體 (非抽象) 類別。 您可以使用原來的具體類別，或在許多狀況中從它們衍生您自己的類別。 若要使用介面的功能，您可以建立實作介面的類別，或者從實作介面的 .NET Framework 類別之一來衍生類別。  
  
## <a name="naming-conventions"></a>命名規範  
 .NET Framework 型別使用意味著階層架構的點語法命名配置。 這個技術將相關的型別群組至命名空間 (Namespace)，所以可以更容易地搜尋和參考它們。 完整名稱的第一部分 - 直到最右邊的點 - 是命名空間名稱。 最後部分是型別名稱。 例如，**System.Collections.ArrayList** 代表 **ArrayList** 類型，其屬於 **System.Collections** 命名空間。 **System.Collections** 中的類型可以用來操作物件的集合。  
  
 這個命名配置使得程式庫開發人員更容易擴充 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 以建立階層式型別群組，並以一致且有意義的方式來命名它們。 此外還允許以完整名稱明確識別型別 (也就是藉由命名空間和型別名稱)，其可避免型別名稱衝突。 程式庫開發人員為其命名空間建立名稱時，應使用以下命名慣例：  
  
 *CompanyName*.*TechnologyName*  
  
 例如，Microsoft.Word 命名空間符合這個方針。  
  
 使用命名模式將相關的型別群組至命名空間，是建置和記錄類別庫非常有用的方式。 然而，這個命名配置在可視性、成員存取、繼承 (Inheritance)、安全性或繫結上沒有作用。 命名空間可以在多重組件 (Assembly) 之間分割，而單一組件可以包含來自多重命名空間的型別。 組件在 Common Language Runtime 中提供版本、部署、安全性、載入和可視性的正式結構。  
  
 如需命名空間和類型名稱的詳細資訊，請參閱[一般型別系統](../../docs/standard/base-types/common-type-system.md)。  
  
## <a name="system-namespace"></a>System 命名空間  
 <xref:System> 命名空間是 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中基礎型別的根 (Root) 命名空間。 這個命名空間包含的類別，代表所有應用程式使用的基底資料型別：<xref:System.Object> (繼承階層架構的根)、<xref:System.Byte>、<xref:System.Char>、<xref:System.Array>、<xref:System.Int32>、<xref:System.String> 等等。 許多這些型別對應到您的程式語言所使用的原始資料型別。 當您使用 .NET Framework 型別撰寫程式碼時，您可以在需要 .NET Framework 基底資料型別時使用您語言的對應關鍵字。  
  
 下表列出 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 所提供基底型別的清單、簡要說明各型別，並且指示 Visual Basic、C#、C++ 和 JScript 中的對應型別。  
  
|分類|類別名稱|描述|Visual Basic 資料型別|C# 資料型別|C++ 資料型別|JScript 資料型別|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|整數|<xref:System.Byte>|8 位元不帶正負號的整數。|**Byte**|**byte**|**unsigned char**|**Byte**|  
||<xref:System.SByte>|8 位元帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**SByte**|**sbyte**|**char**<br /><br /> -或-<br /><br /> **signed** **char**|**SByte**|  
||<xref:System.Int16>|16 位元帶正負號的整數。|**Short**|**short**|**short**|**short**|  
||<xref:System.Int32>|32 位元帶正負號的整數。|**Integer**|**int**|**int**<br /><br /> -或-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64 位元帶正負號的整數。|**Long**|**long**|**__int64**|**long**|  
||<xref:System.UInt16>|16 位元不帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**UShort**|**ushort**|**unsigned short**|**UInt16**|  
||<xref:System.UInt32>|32 位元不帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**UInteger**|**uint**|**unsigned int**<br /><br /> -或-<br /><br /> **unsigned long**|**UInt32**|  
||<xref:System.UInt64>|64 位元不帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**ULong**|**ulong**|**unsigned __int64**|**UInt64**|  
|浮點|<xref:System.Single>|單精確度 (32 位元) 浮點數。|**Single**|**float**|**float**|**float**|  
||<xref:System.Double>|雙精度 (64 位元) 浮點數。|**Double**|**double**|**double**|**double**|  
|邏輯|<xref:System.Boolean>|布林值 (true 或 false)。|**布林值**|**bool**|**bool**|**bool**|  
|其他|<xref:System.Char>|Unicode (16 位元) 字元。|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|這是一個 128 位元的十進位值。|**Decimal**|**decimal**|**Decimal**|**Decimal**|  
||<xref:System.IntPtr>|帶正負號的整數，其大小取決於基礎平台 (在 32 位元平台為 32 位元值，而在 64 位元平台為 64 位元值)。|**IntPtr**<br /><br /> 非內建型別|**IntPtr**<br /><br /> 非內建型別|**IntPtr**<br /><br /> 非內建型別|**IntPtr**|  
||<xref:System.UIntPtr>|不帶正負號的整數，其大小取決於基礎平台 (在 32 位元平台為 32 位元值，而在 64 位元平台為 64 位元值)。<br /><br /> 不符合 CLS 標準。|**UIntPtr**<br /><br /> 非內建型別|**UIntPtr**<br /><br /> 非內建型別|**UIntPtr**<br /><br /> 非內建型別|**UIntPtr**|  
ass 物件|<xref:System.Object>|物件階層架構的根。|**物件**|**object**|**Object\***|**物件**|  
||<xref:System.String>|Unicode 字元，為不變且長度固定的字串。|**String**|**string**|**String\***|**String**|  
  
 除了基底資料型別，<xref:System> 命名空間還包含 100 多個類別，涵蓋的範圍從處理例外狀況的類別到處理核心執行階段概念的類別，像是應用程式定義域和記憶體回收行程。 <xref:System> 命名空間也包含許多第二層命名空間。  
  
 如需命名空間的詳細資訊，請瀏覽 [.NET Framework Class Library](http://go.microsoft.com/fwlink/?LinkID=227195) (.NET Framework 類別庫)。 參考文件提供各個命名空間的簡要概觀，還有各個型別和它成員的正式說明。  
  
## <a name="see-also"></a>另請參閱  
 [一般類型系統](../../docs/standard/base-types/common-type-system.md)  
 [.NET Framework 類別庫](http://go.microsoft.com/fwlink/?LinkID=227195)  
 [概觀](../../docs/framework/get-started/overview.md)
