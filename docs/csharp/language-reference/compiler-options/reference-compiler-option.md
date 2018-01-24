---
title: "-reference (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 60a00b1cd088a051e1a58d245c455b9678a74988
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-reference-c-compiler-options"></a>-reference (C# 編譯器選項)
**-reference** 選項可讓編譯器將指定檔案的 [public](../../../csharp/language-reference/keywords/public.md) 類型資訊匯入至目前的專案，以讓您透過指定的組件檔案來參考中繼資料。  
  
## <a name="syntax"></a>語法  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 含有組件資訊清單 (Assembly Manifest) 的檔案名稱。 若要匯入多個檔案，請為每個檔案納入個別的 **-reference** 選項。  
  
 `alias`  
 有效的 C# 識別項，代表包含組件中所有命名空間的根命名空間。  
  
## <a name="remarks"></a>備註  
 若要從多個檔案進行匯入，請為每個檔案納入 **-reference** 選項。  
  
 您匯入的檔案必須包含資訊清單，且輸出檔案必須已使用其中一個 [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項進行編譯 ([-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 除外)。  
  
 **-r** 是 **-reference** 的簡短形式。  
  
 如果輸出檔案不包含組件資訊清單，請使用 [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) 以從中匯入中繼資料。  
  
 如果您參考的組件 (組件 A) 有參考其他組件 (組件 B)，則在下列情況中，您也需要參考 B 組件：  
  
-   您使用的類型是來自組件 A，但繼承自組件 B 的類型，或是實作組件 B 的介面。  
  
-   您所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。  
  
 使用 [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)，以指定一或多個組件參考所在的目錄。 **-lib** 主題也會說明編譯器會在其中搜尋組件的目錄。  
  
 為了讓編譯器可以辨識位於組件中的類型 (而不是模組中)，您必須定義類型的執行個體，以強制讓編譯器解析類型。 您也可以使用其他方法，讓編譯器解析組件中的類型名稱：例如，您可以繼承組件的類型，編譯器即可辨識類型名稱。  
  
 有時候，您必須參考組件內相同元件的兩個不同版本。 若要這樣做，請針對每個檔案，使用 **-reference** 參數上的別名子選項，以區別兩個不同的檔案。 系統會將此別名作為元件名稱的限定詞，並將元件解析為其中一個檔案。  
  
 預設會使用 csc 回應檔 (.rsp)，以參考常用的 .NET Framework 組件。 如果您不想讓編譯器使用 csc.rsp，可使用 [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)。  
  
> [!NOTE]
> 在 Visual Studio 中，使用 [新增參考] 對話方塊。 如需詳細資訊，請參閱[如何：使用參考管理員新增或移除參考](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。 新增參考時，為了確保使用 `-reference` 以及使用 [新增參考] 對話方塊的對等行為，請將您要新增之組件的 [內嵌 Interop 類型] 屬性設為 **False**。 這個屬性的預設值為 **True**。  
  
## <a name="example"></a>範例  
 這個範例會示範如何使用[外部別名](../../../csharp/language-reference/keywords/extern-alias.md)功能。  
  
 您可以編譯原始程式檔，並從之前已編譯過的 `grid.dll` 和 `grid20.dll` 匯入中繼資料。 這兩個 DLL 包含相同元件的不同版本，因此您需要搭配使用兩個 **-reference** 與別名選項，來編譯原始程式檔。 選項應該看起來像這樣︰  
  
 -reference:GridV1=grid.dll 和 -reference:GridV2=grid20.dll  
  
 這會設定 "GridV1" 和 "GridV2" 外部別名，您可透過 extern 陳述式以在程式中使用這些別名：  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 完成之後，您可以在 GridV1 前面加上控制項名稱，以參照 grid.dll 的方格控制項，如下所示：  
  
```csharp  
GridV1::Grid  
```  
  
 此外，您可以在 GridV2 前面加上控制項名稱，以參照 grid20.dll 的方格控制項，如下所示：  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
