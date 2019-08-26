---
title: 範例 COM 類別 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 461d5a2afb197596c1c52daeeca0583b7b5e9693
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589149"
---
# <a name="example-com-class-c-programming-guide"></a>範例 COM 類別 (C# 程式設計手冊)
以下是公開為 COM 物件類別的範例。 在此程式碼放入 .cs 檔案並新增至專案之後，將**註冊 COM Interop** 屬性設定為 **True**。 如需詳細資訊，請參閱[如何：為元件註冊 COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))。
  
 將 Visual C# 物件公開給 COM 需要宣告類別介面和類別本身，以及事件介面 (若需要)。 類別成員必須遵守下列規則才能為 COM 所見︰  
  
- 類別必須是公用的。  
  
- 屬性、方法及事件必須是公用的。  
  
- 必須在類別介面上宣告屬性和方法。  
  
- 必須在事件介面中宣告事件。  
  
 未在這些介面中宣告的類別其他公用成員不會為 COM 所見，但會向其他 .NET Framework 物件顯示。  
  
 若要向 COM 公開屬性和方法，您必須在類別介面上宣告它們，並以 `DispId` 屬性標記它們，然後在類別中實作它們。 成員在介面中的宣告順序是 COM vtable 使用的順序。  
  
 若要從您的類別公開事件，您必須在事件介面上宣告它們，並使用 `DispId` 屬性標記它們。 此類別不應該實作這個介面。  
  
 類別會實作類別介面，它可以實作多個介面，但首次實作是在預設類別介面。 實作此處向 COM 公開的方法和屬性。 它們必須標示為公用，且必須符合類別介面中的宣告。 此外，宣告類別在此引發的事件。 它們必須標示為公用，且必須符合事件介面中的宣告。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [互通性](./index.md)
- [專案設計工具、建置頁面 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
