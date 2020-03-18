---
title: 組件內容
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75345579"
---
# <a name="assembly-contents"></a>組件內容

一般而言，靜態組件可包含四個項目：

- [組件資訊清單](manifest.md)，其中含有組件中繼資料。

- 型別中繼資料  

- 會實作型別的 Microsoft Intermediate Language (MSIL) 程式碼 它由編譯器從一個或多個原始程式碼檔生成。

- 一組[資源](../../framework/resources/index.md)。  

只有組件資訊清單是必要項，不過型別或資源兩者必須有一項要用來賦予組件任何有意義的功能。

下圖顯示了這些元素分組到單個物理檔中：

![稱為 MyAssembly.dll 的單檔程式集](./media/contents/single-file-assembly.gif)

在設計原始程式碼時，您可以就如何將應用程式的功能分區為一個或多個檔做出明確決策。 設計 .NET 代碼時，您將就如何將功能分區為一個或多個程式集做出類似的決策。

## <a name="see-also"></a>另請參閱

- [.NET 中的組件](index.md)
- [組件資訊清單](manifest.md)
- [組件安全性考量](security-considerations.md)
