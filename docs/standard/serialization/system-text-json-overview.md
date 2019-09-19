---
title: .NET 中的 JSON 序列化
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083088"
---
# <a name="json-serialization-in-net"></a>.NET 中的 JSON 序列化

命名`System.Text.Json`空間提供在 JavaScript 物件標記法（JSON）中進行序列化的功能。

程式庫設計強調廣泛功能集的高效能和低記憶體配置。 內建的 UTF-8 支援將讀取和寫入 JSON 文字編碼為 UTF-8 的程式優化，這對網路上的資料和磁片上的檔案而言是最普遍的編碼方式。

程式庫也會提供類別，以使用記憶體中的檔物件模型（DOM）。 這項功能可讓您對 JSON 檔案或字串中的元素進行隨機唯讀存取。 

## <a name="how-to-get-the-library"></a>如何取得程式庫

* 此程式庫內建為[.Net Core 3.0](https://aka.ms/netcore3download)共用架構的一部分。
* 若是其他目標 framework，請安裝[System.web](https://www.nuget.org/packages/System.Text.Json) NuGet 封裝。 封裝支援：
  * .NET Standard 2.0 和更新版本
  * .NET Framework 4.61 和更新版本
  * .NET Core 2.0 和更新版本

## <a name="additional-resources"></a>其他資源

* [如何使用程式庫](system-text-json-how-to.md)
* [原始程式碼 (英文)](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [API 參考](xref:System.Text.Json)
* [藍圖](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Dotnet/corefx 存放庫中的 GitHub 問題
  * [有關如何開發 System.web 的討論](https://github.com/dotnet/corefx/issues/33115)
  * [所有的 System.object 問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [已標記 json 的 system.object 問題-功能-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
