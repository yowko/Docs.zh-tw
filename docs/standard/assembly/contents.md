---
title: 組件內容
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 9ca12ee4bd993db3dd200a3b340c220ce5188796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122541"
---
# <a name="assembly-contents"></a>組件內容
一般而言，靜態組件可包含四個項目：

- [組件資訊清單](manifest.md)，其中含有組件中繼資料。

- 型別中繼資料  

- 會實作型別的 Microsoft Intermediate Language (MSIL) 程式碼 它是由編譯器從一或多個原始程式碼檔所產生。

- 資源集合  

只有組件資訊清單是必要項，不過型別或資源兩者必須有一項要用來賦予組件任何有意義的功能。

下圖顯示在單一實體檔案中分組的這些元素。

![顯示稱為 MyAssembly.dll 之單一檔案組件的圖表。](./media/contents/single-file-assembly.gif)

在這個圖中，這三個檔案都屬於一個組件，如同 MyAssembly.dll 中所含組件資訊清單中的描述。 對於檔案系統而言，它們是三個不同的檔案。 請注意，Util.netmodule 這個檔案會編譯為模組，這是因為它並不包含組件資訊。 建立這個組件時，已將組件資訊清單加入至 MyAssembly.dll 中，指出它與 Util.netmodule 和 Graphic.bmp 的關聯性。

目前在設計原始程式碼時，您必須明確決定要如何將應用程式的功能分割在一個或多個檔案中。 在設計 .NET Framework 程式碼時，您也必須做出如何將功能分割為一個或多個組件的類似決定。

## <a name="see-also"></a>請參閱

- [.NET 中的組件](index.md)
- [組件資訊清單](manifest.md)
- [元件安全性考慮](security-considerations.md)
