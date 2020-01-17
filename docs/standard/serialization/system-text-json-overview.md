---
title: 使用C# -.net 序列化和還原序列化 JSON
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: acb83be9b20a155b6b6a9fb5ade38e099f54e71d
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163588"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>.NET 中的 JSON 序列化和還原序列化（封送處理和 unmarshalling）-總覽

`System.Text.Json` 命名空間提供從 JavaScript 物件標記法（JSON）序列化及還原序列化的功能。

程式庫設計強調廣泛功能集的高效能和低記憶體配置。 內建的 UTF-8 支援將讀取和寫入 JSON 文字編碼為 UTF-8 的程式優化，這對網路上的資料和磁片上的檔案而言是最普遍的編碼方式。

程式庫也會提供類別，以使用記憶體中的檔物件模型（DOM）。 這項功能可讓您對 JSON 檔案或字串中的元素進行隨機唯讀存取。 

## <a name="how-to-get-the-library"></a>如何取得程式庫

* 此程式庫內建為[.Net Core 3.0](https://aka.ms/netcore3download)共用架構的一部分。
* 若為其他目標 framework，請安裝[System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 套件。 封裝支援：
  * .NET Standard 2.0 和更新版本
  * .NET Framework 4.7.2 和更新版本
  * .NET Core 2.0、2.1 和2.2

## <a name="additional-resources"></a>其他資源

* [如何使用程式庫](system-text-json-how-to.md)
* [如何從 Newtonsoft.Json 遷移](system-text-json-migrate-from-newtonsoft-how-to.md)
* [如何撰寫轉換器](system-text-json-converters-how-to.md)
* [System.Text.Json 原始碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json。序列化 API 參考](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
