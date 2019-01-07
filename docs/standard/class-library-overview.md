---
title: .NET 類別庫概觀
ms.date: 02/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], library overview
- classes [.NET Core], library overview
- .NET, library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], F#
- System namespace
- F#, data types
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b00d08f43874518e117739d4a9502bf9463db5c1
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029866"
---
# <a name="net-class-library-overview"></a>.NET 類別庫概觀

.NET 實作包括類別、介面、委派和實值型別，以加速和最佳化開發過程並提供對系統功能的存取。 為了促進語言之間的互通性，大部分 .NET 類型符合 CLS 標準，因而可以透過其編譯器符合 Common Language Specification (CLS) 的任何程式設計語言來使用。  
  
 .NET 類型是建置 .NET 應用程式、元件和控制項的基礎。 .NET 實作包含執行下列函式的類型：  
  
-   代表基底資料型別和例外狀況  
  
-   封裝資料結構  
  
-   執行 I/O  
  
-   存取有關已載入型別的資訊  
  
-   叫用 .NET Framework 安全性檢查  
  
-   提供資料存取、豐富型用戶端 (Rich Client) GUI 和伺服器控制的用戶端 GUI  
  
 .NET 提供相當豐富的介面，以及抽象和具體 (非抽象) 類別。 您可以使用原來的具體類別，或在許多狀況中從它們衍生您自己的類別。 若要使用介面的功能，您可以建立實作介面的類別，或者從實作介面的 .NET 類別之一來衍生類別。  
  
## <a name="naming-conventions"></a>命名規範

 .NET 類型使用意味著階層架構的點語法命名配置。 這個技術將相關的型別群組至命名空間 (Namespace)，所以可以更容易地搜尋和參考它們。 完整名稱的第一部分 - 直到最右邊的點 - 是命名空間名稱。 最後部分是型別名稱。 例如，`System.Collections.Generic.List<T>` 代表 `List<T>` 型別，其屬於 `System.Collections.Generic` 命名空間。 <xref:System.Collections.Generic> 中的型別可以用來處理泛型集合。  
  
 這個命名配置使得程式庫開發人員更容易擴充 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 以建立階層式型別群組，並以一致且有意義的方式來命名它們。 此外還允許以完整名稱明確識別型別 (也就是藉由命名空間和型別名稱)，其可避免型別名稱衝突。 程式庫開發人員為其命名空間建立名稱時，應使用以下命名慣例：  
  
 *CompanyName*.*TechnologyName*  
  
 例如，`Microsoft.Word`　命名空間符合這個方針。  
  
 使用命名模式將相關的型別群組至命名空間，是建置和記錄類別庫非常有用的方式。 然而，這個命名配置在可視性、成員存取、繼承 (Inheritance)、安全性或繫結上沒有作用。 命名空間可以在多重組件 (Assembly) 之間分割，而單一組件可以包含來自多重命名空間的型別。 組件在 Common Language Runtime 中提供版本、部署、安全性、載入和可視性的正式結構。  
  
 如需命名空間和類型名稱的詳細資訊，請參閱[一般型別系統](../../docs/standard/base-types/common-type-system.md)。  
  
## <a name="system-namespace"></a>System 命名空間

 <xref:System> 命名空間是 .NET 中基本類型的根命名空間。 這個命名空間包含的類別，代表所有應用程式使用的基底資料型別：<xref:System.Object> (繼承階層架構的根)、<xref:System.Byte>、<xref:System.Char>、<xref:System.Array>、<xref:System.Int32>、<xref:System.String> 等等。 許多這些型別對應到您的程式語言所使用的原始資料型別。 當您使用 .NET Framework 型別撰寫程式碼時，您可以在需要 .NET Framework 基底資料型別時使用您語言的對應關鍵字。  
  
 下表列出 .NET 所提供基底類型的清單、簡要描述各類型，並且指示 Visual Basic、C#、C++ 和 F# 中的對應類型。  
  
|分類|類別名稱|說明|Visual Basic 資料型別|C# 資料型別|C++/CLI 資料類型|F# 資料類型|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|整數|<xref:System.Byte>|8 位元不帶正負號的整數。|**Byte**|**byte**|**unsigned char**|**byte**|  
||<xref:System.SByte>|8 位元帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**SByte**|**sbyte**|**char**<br /> -或-<br /> **signed** **char**|**sbyte**|  
||<xref:System.Int16>|16 位元帶正負號的整數。|**Short**|**short**|**short**|**int16**|  
||<xref:System.Int32>|32 位元帶正負號的整數。|**Integer**|**int**|**int**<br /><br /> -或-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64 位元帶正負號的整數。|**Long**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|16 位元不帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**UShort**|**ushort**|**unsigned short**|**uint16**|  
||<xref:System.UInt32>|32 位元不帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**UInteger**|**uint**|**unsigned int**<br /> -或-<br /> **unsigned long**|**uint32**|  
||<xref:System.UInt64>|64 位元不帶正負號的整數。<br /><br /> 不符合 CLS 標準。|**ULong**|**ulong**|**unsigned __int64**|**uint64**|  
|浮點|<xref:System.Single>|單精確度 (32 位元) 浮點數。|**Single**|**float**|**float**|**float32**</br> 或</br>**single**|  
||<xref:System.Double>|雙精度 (64 位元) 浮點數。|**Double**|**double**|**double**|**float**</br> 或 </br> **double**|  
|邏輯|<xref:System.Boolean>|布林值 (true 或 false)。|**布林值**|**bool**|**bool**|**bool**|  
|其他|<xref:System.Char>|Unicode (16 位元) 字元。|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|這是一個 128 位元的十進位值。|**Decimal**|**decimal**|**Decimal**|**decimal**|  
||<xref:System.IntPtr>|帶正負號的整數，其大小取決於基礎平台 (在 32 位元平台為 32 位元值，而在 64 位元平台為 64 位元值)。|**IntPtr**<br /><br /> 非內建型別|**IntPtr**<br /><br /> 非內建型別|**IntPtr**<br /><br /> 非內建型別|**unativeint**|  
||<xref:System.UIntPtr>|不帶正負號的整數，其大小取決於基礎平台 (在 32 位元平台為 32 位元值，而在 64 位元平台為 64 位元值)。<br /><br /> 不符合 CLS 標準。|**UIntPtr**<br /><br /> 非內建型別|**UIntPtr**<br /><br /> 非內建型別|**UIntPtr**<br /><br /> 非內建型別|**unativeint**|  
||<xref:System.Object>|物件階層架構的根。|**物件**|**object**|**Object^**|**obj**|  
||<xref:System.String>|Unicode 字元，為不變且長度固定的字串。|**String**|**string**|**String^**|**string**|  
  
 除了基底資料型別，<xref:System> 命名空間還包含 100 多個類別，涵蓋的範圍從處理例外狀況的類別到處理核心執行階段概念的類別，像是應用程式定義域和記憶體回收行程。 <xref:System> 命名空間也包含許多第二層命名空間。  
  
 如需命名空間的詳細資訊，請使用 [.NET API 瀏覽器](https://docs.microsoft.com/dotnet/api)來瀏覽 .NET 類別庫。 API 參考文件提供每個命名空間、其類型及其每個成員的相關文件。  
  
## <a name="see-also"></a>另請參閱

- [一般類型系統](../../docs/standard/base-types/common-type-system.md)  
- [.NET API 瀏覽器](../../api/index.md)  
- [概觀](../../docs/framework/get-started/overview.md)
