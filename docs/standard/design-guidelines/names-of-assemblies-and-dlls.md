---
title: 組件和 DLL 的名稱
description: 瞭解命名元件和動態連結程式庫（Dll）的指導方針。 元件可以跨越一個或多個檔案，但它通常會與 DLL 對應一對一。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: de7ce3ee774d4598521d7156d0d660c3fe30154c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594474"
---
# <a name="names-of-assemblies-and-dlls"></a>組件和 DLL 的名稱
「元件」（assembly）是受控碼程式的部署和身分識別單位。 雖然元件可以跨越一個或多個檔案，但通常元件會與 DLL 對應一對一。 因此，本節只會描述 DLL 命名慣例，然後對應至元件命名慣例。

 ✔️確實會針對您的元件 Dll 選擇名稱，以建議很大的功能區塊，例如 System.object。

 元件和 DLL 名稱不一定要對應至命名空間名稱，但在命名元件時，可以合理遵循命名空間名稱。 理想的經驗法則是根據元件中所含命名空間的通用前置詞來命名 DLL。 例如，可以呼叫具有兩個命名空間 `MyCompany.MyTechnology.FirstFeature` 和的元件 `MyCompany.MyTechnology.SecondFeature` `MyCompany.MyTechnology.dll` 。

 ✔️考慮根據下列模式來命名 Dll：

 `<Company>.<Component>.dll`

 其中 `<Component>` 包含一或多個以點分隔的子句。 例如：

 `Litware.Controls.dll`.

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>請參閱

- [架構設計方針](index.md)
- [命名方針](naming-guidelines.md)
