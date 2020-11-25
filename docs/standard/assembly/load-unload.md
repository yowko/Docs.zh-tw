---
title: 如何：載入和卸載元件
description: CLR 會自動載入程式所參考的 .NET 元件。 您也可以將特定的元件動態載入至目前的應用程式域。
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: fe1a5fe63361620f8ab99ec8469169ed2213c0ee
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731484"
---
# <a name="how-to-load-and-unload-assemblies"></a>如何：載入和卸載元件

Common language runtime 會自動載入程式所參考的元件，但也可以將特定的元件動態載入至目前的應用程式域。 如需詳細資訊，請參閱 [如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。

在 .NET Framework 中，沒有任何方法可卸載個別的元件，而不需要卸載所有包含該元件的應用程式域。 即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。 在 .NET Core 中， <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> 類別會處理元件的卸載。 如需詳細資訊，請參閱 [如何在 .Net Core 中使用和偵錯工具集卸載功能](unloadability.md)。

## <a name="load-and-unload-assemblies"></a>載入和卸載組件

若要將元件載入應用程式域，請使用類別和中包含的數個載入方法 <xref:System.AppDomain> 之一 <xref:System.Reflection.Assembly> 。 如需詳細資訊，請參閱 [如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。 請注意，.NET Core 僅支援單一應用程式域。

若要卸載 .NET Framework 中的元件，您必須卸載所有包含該元件的應用程式域。 若要卸載應用程式域，請使用 <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 方法。 如需詳細資訊，請參閱 [如何：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。

如果您想要卸載某些元件，而不是 .NET Framework 應用程式中的其他元件，請考慮建立新的應用程式域、在該網域內執行程式碼，然後再卸載該應用程式域。 如需詳細資訊，請參閱 [如何：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。  

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../../csharp/programming-guide/index.md)
- [ (Visual Basic) 的程式設計概念 ](../../visual-basic/programming-guide/concepts/index.md)
- [.NET 中的組件](index.md)
- [如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
