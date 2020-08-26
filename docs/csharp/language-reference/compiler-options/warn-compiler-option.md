---
title: -warn (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: d495ef76dc390d8dd2a361d5530f9e39d7128b3e
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867603"
---
# <a name="-warn-c-compiler-options"></a>-warn (C# 編譯器選項)
**-warn** 選項指定要針對編譯器顯示的警告層級。  
  
## <a name="syntax"></a>語法  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>引數  
 `option`  
 您想要針對編譯顯示的警告層級：較低的數字只會顯示高嚴重性警告；較高的數字則顯示更多的警告。 此值必須為零或正整數：

|警告層級|意義|
|-------------------|-------------|
|0|關閉發出所有警告訊息。|
|1|顯示嚴重警告訊息。|  
|2|顯示層級 1 警告，以及特定較不嚴重的警告，例如隱藏類別成員的警告。|  
|3|顯示層級 2 警告，以及特定較不嚴重的警告，例如一律評估為 `true` 或 `false` 之運算式的警告。|  
|4 (預設值)|顯示所有層級 3 警告以及告知性警告。|
|5|顯示層級4警告以及編譯器隨附的 [其他警告](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) （c # 9.0）。|
|大於5|任何大於5的值都會被視為5。 您通常會將任意大數值 (例如， `9999`) ，以確保當編譯器以新的警告層級更新時，一律會出現所有警告。|
  
## <a name="remarks"></a>備註  
 若要取得錯誤或警告資訊，您可以查閱 [說明索引] 中的錯誤碼。 如需取得錯誤或警告資訊的其他方式，請參閱 [C# 編譯器錯誤](../compiler-messages/index.md)。  
  
 使用 [-warnaserror](./warnaserror-compiler-option.md) 將所有警告都視為錯誤。 使用 [-nowarn](./nowarn-compiler-option.md) 停用特定警告。  
  
 **-w** 是 **-warn** 的簡短形式。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟專案的 [屬性]**** 頁面。  
  
2. 按一下 [建置]**** 屬性頁面。  
  
3. 修改 [警告層級]**** 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>。  
  
## <a name="example"></a>範例  
 編譯 `in.cs`，並讓編譯器只顯示層級 1 警告：  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>請參閱

- [C # 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
