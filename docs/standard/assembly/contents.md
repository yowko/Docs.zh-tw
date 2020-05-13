---
title: 組件內容
description: 本文描述 .NET 元件的內容，其中可能包括元件中繼資料、類型中繼資料、MSIL 程式碼和資源。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 94df452162ed7290fab7fa267d2624e6d844a587
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378573"
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
- [組件安全性考量](security-considerations.md)
