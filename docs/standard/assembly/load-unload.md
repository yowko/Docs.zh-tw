---
title: 作法：載入和卸載元件
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973198"
---
# <a name="how-to-load-and-unload-assemblies"></a>作法：載入和卸載元件
通用語言執行平臺會自動載入程式所參考的元件，但也可以動態地將特定元件載入目前的應用程式域中。 如需詳細資訊，請參閱[如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)中。

在 .NET Framework 中，沒有任何方法可以卸載個別元件，而不需卸載包含它的所有應用程式域。 即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。 在 .net Core 中， <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType>類別會處理元件的卸載。 如需詳細資訊，請參閱[如何在 .Net Core 中使用和偵錯工具元件卸載功能](unloadability.md)。

## <a name="load-and-unload-assemblies"></a>載入和卸載元件

若要將元件載入應用程式域，請使用類別<xref:System.AppDomain>和<xref:System.Reflection.Assembly>中包含的數個 load 方法其中之一。 如需詳細資訊，請參閱[如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)中。 請注意，.NET Core 僅支援單一應用程式域。 

若要卸載 .NET Framework 中的元件，您必須卸載包含它的所有應用程式域。 若要卸載應用程式域，請<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>使用方法。 如需詳細資訊，請參閱[如何：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。

如果您想要卸載某些元件，而不是 .NET Framework 應用程式中的其他元件，請考慮建立新的應用程式域，並在該網域內執行程式碼，然後再卸載該應用程式域。 如需詳細資訊，請參閱[如何：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。  

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（Visual Basic）](../../visual-basic/programming-guide/concepts/index.md)
- [.NET 中的組件](index.md)
- [如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
