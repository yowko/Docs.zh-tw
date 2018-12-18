---
title: Framework 程式庫
description: 了解這些程式庫如何提供許多一般和應用程式特定類型、演算法，以及公用程式功能的實作。
author: richlander
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: b3cfc44c430a02ec9ffce75ebff5c8f9cc46505c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143372"
---
# <a name="framework-libraries"></a>Framework 程式庫

.NET 有一組可擴充的標準類別庫，稱為基底類別庫 (核心集合) 或 Framework Class Library (完整集合)。 這些程式庫提供許多一般和應用程式特定類型、演算法，以及公用程式功能的實作。 商業和社群程式庫都是以 Framework Class Library 為建置基礎，因此可讓您輕鬆地使用現成的程式庫，來執行一組廣泛的運算工作。

每個 .NET 實作都會提供這些程式庫的子集。 任何 .NET 實作都必須有基底類別庫 (BCL) API，除了因為開發人員需要之外，也因為熱門程式庫需要此 API 才能執行。 並非所有 .NET 實作都會在 BCL 上提供應用程式特定的程式庫 (例如 ASP.NET)。

## <a name="base-class-libraries"></a>基底類別庫

BCL 提供最基本的類型和公用程式功能，是所有其他 .NET 類別庫的基礎。 其目標在於提供非常通用的實作，所有工作負載皆一視同仁。 效能一律是很重要的考量，因為應用程式可能偏好某項原則，例如偏好低延遲而不是高輸送量，或偏好低記憶體而不是低 CPU 使用量。 這些程式庫的效能普遍都很高，並根據各種效能考量採取折衷方法。 對於大多數應用程式而言，此方法一直以來都相當成功。

## <a name="primitive-types"></a>基本類型

.NET 包含一組所有程式 (在某種程度上) 都會使用的基本類型。 這些類型包含資料，例如數字、字串、位元組和任意物件。 C# 語言包含這些類型的關鍵字。 以下列出一組範例類型，並提供相符的 C# 關鍵字。

* <xref:System.Object?displayProperty=nameWithType> ([object](../csharp/language-reference/keywords/object.md)) - CLR 型別系統中的 Ultimate 基底類別。 它是類型階層架構中的根類型。
* <xref:System.Int16?displayProperty=nameWithType> ([short](../csharp/language-reference/keywords/short.md)) - 16 位元帶正負號的整數類型。 也存在不帶正負號的 <xref:System.UInt16>。
* <xref:System.Int32?displayProperty=nameWithType> ([int](../csharp/language-reference/keywords/int.md)) - 32 位元帶正負號的整數類型。 也存在不帶正負號的 [UInt32](../csharp/language-reference/keywords/uint.md)。
* <xref:System.Single?displayProperty=nameWithType> ([float](../csharp/language-reference/keywords/float.md)) - 32 位元浮點類型。
* <xref:System.Decimal?displayProperty=nameWithType> ([decimal](../csharp/language-reference/keywords/decimal.md)) - 128 位元 Decimal 類型。
* <xref:System.Byte?displayProperty=nameWithType> ([byte](../csharp/language-reference/keywords/byte.md)) - 代表記憶體位元組之不帶正負號的 8 位元整數。
* <xref:System.Boolean?displayProperty=nameWithType> ([bool](../csharp/language-reference/keywords/bool.md)) - 代表 `true` 或 `false` 的布林類型。
* <xref:System.Char?displayProperty=nameWithType> ([char](../csharp/language-reference/keywords/char.md)) - 代表 Unicode 字元的 16 位元數值類型。
* <xref:System.String?displayProperty=nameWithType> ([string](../csharp/language-reference/keywords/string.md)) - 代表連續字元。 不同於 `char[]`，但允許編製索引為 `string` 中的每個 `char`。

## <a name="data-structures"></a>資料結構

.NET 包含一組可承載幾乎所有 .NET 應用程式的資料結構。 其中大多是集合，但也包含其他類型。

*   <xref:System.Array> - 代表可依索引存取的強型別物件陣列。 根據其建構具有固定大小。
*   <xref:System.Collections.Generic.List%601> - 代表可依索引存取的強型別物件清單。 其大小會視需要自動調整。
*   <xref:System.Collections.Generic.Dictionary%602> - 代表由索引鍵編製索引的值集合。 這些值可透過索引鍵存取。 其大小會視需要自動調整。
*   <xref:System.Uri> - 提供統一資源識別項 (URI) 的物件表示，以及對 URI 各部分的簡易存取。
*   <xref:System.DateTime> - 代表時間的瞬間，通常以一天的日期和時間表示。

## <a name="utility-apis"></a>公用程式 API

.NET 包含一組公用程式 API，以提供用於執行許多重要工作的功能。

*   <xref:System.Net.Http.HttpClient> - 此 API 可用於傳送 HTTP 要求，以及從 URI 所識別的資源接收 HTTP 回應。
*   <xref:System.Xml.Linq.XDocument> - 此 API 可用於載入，以及使用 LINQ 查詢 XML 文件。
*   <xref:System.IO.StreamReader> - 此 API 可用於讀取檔案。 
*   <xref:System.IO.StreamWriter> - 此 API 可用於寫入檔案。

## <a name="app-model-apis"></a>應用程式模型 API

有幾家公司提供許多應用程式模型以搭配 .NET 使用。

*   [ASP.NET](https://www.asp.net) - 提供用於建置網站和服務的 Web 架構。 受到 Windows、Linux 和 macOS 的支援 (視 ASP.NET 版本而定)。
