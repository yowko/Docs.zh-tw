---
title: '使用 c # 序列化和還原序列化 JSON-.NET'
description: 本總覽說明在 System.Text.Json .net 中序列化至 JSON 並從 JSON 還原序列化的命名空間功能。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d8bd5bcf78db534bd722972db01253cbd13a7a06
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282409"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>JSON 序列化和還原序列化 (.NET 中的封送處理和 unmarshalling) -總覽

`System.Text.Json`命名空間提供序列化和還原序列化 JavaScript 物件標記法 (JSON) 的功能。

程式庫設計強調大量功能集的高效能和低記憶體配置。 內建的 UTF-8 支援可將讀取和寫入 JSON 文字的程式優化為 UTF-8，這是 web 上的資料和磁片上的檔案最普遍的編碼方式。

此程式庫也會提供類別，以處理記憶體中的檔物件模型 (DOM) 。 這項功能可讓您在 JSON 檔案或字串中啟用元素的隨機唯讀存取。

## <a name="how-to-get-the-library"></a>如何取得程式庫

* 此程式庫內建為適用于 .NET Core 3.0 和更新版本之共用架構的一部分。
* 針對較舊的 framework 版本，請安裝 [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 套件。 封裝支援：

  * .NET Standard 2.0 和更新版本
  * .NET Framework 4.7.2 和更新版本
  * .NET Core 2.0、2.1 和2。2

## <a name="additional-resources"></a>其他資源

* [如何使用程式庫](system-text-json-how-to.md)
* [如何遷移 Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [如何寫入轉換器](system-text-json-converters-how-to.md)
* [System.Text.Json 原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
