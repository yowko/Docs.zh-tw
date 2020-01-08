---
title: 組件內容
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345579"
---
# <a name="assembly-contents"></a>組件內容

一般而言，靜態組件可包含四個項目：

- [組件資訊清單](manifest.md)，其中含有組件中繼資料。

- 型別中繼資料  

- 會實作型別的 Microsoft Intermediate Language (MSIL) 程式碼 它是由編譯器從一或多個原始程式碼檔所產生。

- 一組[資源](../../framework/resources/index.md)。  

只有組件資訊清單是必要項，不過型別或資源兩者必須有一項要用來賦予組件任何有意義的功能。

下圖顯示將這些元素分組成單一實體檔案：

![名為 MyAssembly 的單一檔案元件](./media/contents/single-file-assembly.gif)

當您設計原始程式碼時，您會明確決定如何將應用程式的功能分割成一或多個檔案。 設計 .NET 程式碼時，您將做出類似的決策，說明如何將功能分割成一或多個元件。

## <a name="see-also"></a>請參閱

- [.NET 中的組件](index.md)
- [組件資訊清單](manifest.md)
- [元件安全性考慮](security-considerations.md)
