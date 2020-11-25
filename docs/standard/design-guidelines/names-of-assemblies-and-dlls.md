---
title: 組件和 DLL 的名稱
description: 瞭解 (Dll) 命名元件和動態連結程式庫的指導方針。 元件可以跨越一或多個檔案，但它通常會以一個 DLL 對應到一個或多個檔案。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 95a90ff66ffc9f2a5a3202d6877b1cc19149ff35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706524"
---
# <a name="names-of-assemblies-and-dlls"></a>組件和 DLL 的名稱

元件是 managed 程式碼程式的部署和身分識別單位。 雖然元件可以跨越一或多個檔案，但通常元件會以一個 DLL 對應到一個元件。 因此，本節只會說明 DLL 命名慣例，然後可以對應至元件命名慣例。

 ✔️請選擇您的元件 Dll 名稱，以建議大量的功能，例如 System.object。

 元件和 DLL 名稱不一定要對應至命名空間名稱，但在命名元件時，請遵循命名空間名稱。 理想的經驗法則是根據元件中包含的命名空間一般前置詞來命名 DLL。 例如，有兩個命名空間和的 `MyCompany.MyTechnology.FirstFeature` 元件 `MyCompany.MyTechnology.SecondFeature` 可以被呼叫 `MyCompany.MyTechnology.dll` 。

 ✔️考慮根據下列模式來命名 Dll：

 `<Company>.<Component>.dll`

 其中 `<Component>` 包含一或多個以點分隔的子句。 例如：

 `Litware.Controls.dll`.

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [命名指導方針](naming-guidelines.md)
