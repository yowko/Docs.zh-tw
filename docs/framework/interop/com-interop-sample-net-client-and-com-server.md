---
title: COM Interop 範例：.NET 用戶端與 COM 伺服器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, samples
- COM interop, samples
ms.assetid: a3f752bb-8945-4e1b-8163-71def6e9f137
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddbb7581ab254b428af621bc4412f60aa70bfb08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134520"
---
# <a name="com-interop-sample-net-client-and-com-server"></a><span data-ttu-id="ca33a-102">COM Interop 範例：.NET 用戶端與 COM 伺服器</span><span class="sxs-lookup"><span data-stu-id="ca33a-102">COM Interop Sample: .NET Client and COM Server</span></span>
<span data-ttu-id="ca33a-103">此範例示範建置來存取 [COM 伺服器](#cpconcominteropsamplenetclientcomserveranchor2)的 [.NET 用戶端](#cpconcominteropsamplenetclientcomserveranchor1)如何建立 COM coclass 的執行個體，以及呼叫類別成員來執行貸款計算。</span><span class="sxs-lookup"><span data-stu-id="ca33a-103">This sample demonstrates how a [.NET client](#cpconcominteropsamplenetclientcomserveranchor1), built to access a [COM server](#cpconcominteropsamplenetclientcomserveranchor2), creates an instance of a COM coclass and calls class members to perform mortgage calculations.</span></span>  
  
 <span data-ttu-id="ca33a-104">在此範例中，用戶端會建立和呼叫 **Loan** coclass 執行個體，並將四個引數 (這四個的其中一個等於零) 傳遞給執行個體，然後顯示運算。</span><span class="sxs-lookup"><span data-stu-id="ca33a-104">In this example, the client creates and calls an instance of the **Loan** coclass, passes four arguments (one of those four being equal to zero) to the instance, and displays the computations.</span></span> <span data-ttu-id="ca33a-105">這個範例的程式碼片段會出現在本節中。</span><span class="sxs-lookup"><span data-stu-id="ca33a-105">Code fragments from this sample appear throughout this section.</span></span>  
  
<a name="cpconcominteropsamplenetclientcomserveranchor1"></a>   
## <a name="net-client"></a><span data-ttu-id="ca33a-106">.NET 用戶端</span><span class="sxs-lookup"><span data-stu-id="ca33a-106">.NET Client</span></span>  
  
```vb  
Imports System  
Imports Microsoft.VisualBasic  
Imports LoanLib  
  
Public Class LoanApp  
  
    Public Shared Sub Main()  
        Dim Args As String()  
        Args = System.Environment.GetCommandLineArgs()  
  
        Dim ln As New Loan()  
  
        If Args.Length < 5 Then  
            Console.WriteLine("Usage: ConLoan Balance Rate Term Payment")  
            Console.WriteLine(" Either Balance, Rate, Term, or Payment " _  
                                & "must be 0")  
            Exit Sub  
        End If  
  
        ln.OpeningBalance = Convert.ToDouble(Args(1))  
        ln.Rate = Convert.ToDouble(Args(2)) / 100.0  
        ln.Term = Convert.ToInt16(Args(3))  
        ln.Payment = Convert.ToDouble(Args(4))  
  
        If ln.OpeningBalance = 0.0 Then  
            ln.ComputeOpeningBalance()  
        End If  
        If ln.Rate = 0.0 Then  
            ln.ComputeRate()  
        End If  
        If ln.Term = 0 Then  
            ln.ComputeTerm()  
        End If  
        If ln.Payment = 0.0 Then  
            ln.ComputePayment()  
        End If   
        Console.WriteLine("Balance = {0,10:0.00}", ln.OpeningBalance)  
        Console.WriteLine("Rate    = {0,10:0.0%}", ln.Rate)  
        Console.WriteLine("Term    = {0,10:0.00}", ln.Term)  
        Console.WriteLine("Payment = {0,10:0.00}" & ControlChars.Cr, _  
                          ln.Payment)  
  
        Dim MorePmts As Boolean  
        Dim Balance As Double = 0.0  
        Dim Principal As Double = 0.0  
        Dim Interest As Double = 0.0  
  
        Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", _  
           "Nbr", "Payment", "Principal", "Interest", "Balance")  
        Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", _  
           "---", "-------", "---------", "--------", "-------")  
  
        MorePmts = ln.GetFirstPmtDistribution(ln.Payment, Balance, _  
           Principal, Interest)  
  
        Dim PmtNbr As Short  
  
        While MorePmts  
  
            Console.WriteLine("{0,4}{1,10:0.00}{2,12:0.00}{3,10:0.00}" _  
              & "{4,12:0.00}", PmtNbr, ln.Payment, Principal, Interest,  
              Balance)  
            MorePmts = ln.GetNextPmtDistribution(ln.Payment, Balance, _  
              Principal, Interest)  
            PmtNbr += CShort(1)  
        End While  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using LoanLib;  
  
public class LoanApp {  
   public static void Main(String[] Args) {  
  
      Loan ln = new Loan();  
  
      if (Args.Length < 4)   
      {  
         Console.WriteLine("Usage: ConLoan Balance Rate Term Payment");  
         Console.WriteLine("    Either Balance, Rate, Term, or Payment   
            must be 0");  
         return;  
      }  
  
      ln.OpeningBalance = Convert.ToDouble(Args[0]);  
      ln.Rate = Convert.ToDouble(Args[1])/100.0;  
      ln.Term = Convert.ToInt16(Args[2]);  
      ln.Payment = Convert.ToDouble(Args[3]);  
  
      if (ln.OpeningBalance == 0.00) ln.ComputeOpeningBalance();  
      if (ln.Rate == 0.00) ln.ComputeRate();  
      if (ln.Term == 0) ln.ComputeTerm();  
      if (ln.Payment == 0.00) ln.ComputePayment();  
  
      Console.WriteLine("Balance = {0,10:0.00}", ln.OpeningBalance);  
      Console.WriteLine("Rate    = {0,10:0.0%}", ln.Rate);  
      Console.WriteLine("Term    = {0,10:0.00}", ln.Term);  
      Console.WriteLine("Payment = {0,10:0.00}\n", ln.Payment);  
  
      bool MorePmts;  
      double Balance = 0.0;  
      double Principal = 0.0;  
      double Interest = 0.0;  
  
      Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", "Nbr", "Payment",  
        "Principal", "Interest", "Balance");  
      Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", "---", "-------",  
        "---------", "--------", "-------");  
  
      MorePmts = ln.GetFirstPmtDistribution(ln.Payment, out Balance,   
        out Principal, out Interest);  
  
      for (short PmtNbr = 1; MorePmts; PmtNbr++) {  
         Console.WriteLine("{0,4}{1,10:0.00}{2,12:0.00}{3,10:0.00}  
           {4,12:0.00}", PmtNbr, ln.Payment, Principal, Interest,  
            Balance);  
         MorePmts = ln.GetNextPmtDistribution(ln.Payment, ref Balance,   
           out Principal, out Interest);   
      }  
    }  
}  
```  
  
<a name="cpconcominteropsamplenetclientcomserveranchor2"></a>   
## <a name="com-server"></a><span data-ttu-id="ca33a-107">COM 伺服器</span><span class="sxs-lookup"><span data-stu-id="ca33a-107">COM Server</span></span>  
  
```cpp  
// Loan.cpp : Implementation of CLoan  
#include "stdafx.h"  
#include "math.h"  
#include "LoanLib.h"  
#include "Loan.h"  
  
static double Round(double value, short digits);   
  
STDMETHODIMP CLoan::get_OpeningBalance(double *pVal)  
{  
    *pVal = OpeningBalance;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_OpeningBalance(double newVal)  
{  
    OpeningBalance = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_Rate(double *pVal)  
{  
    *pVal = Rate;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_Rate(double newVal)  
{  
    Rate = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_Payment(double *pVal)  
{  
    *pVal = Payment;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_Payment(double newVal)  
{  
    Payment = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_Term(short *pVal)  
{  
    *pVal = Term;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_Term(short newVal)  
{  
    Term = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputePayment(double *pVal)  
{  
    Payment = Round(OpeningBalance * (Rate /   
        (1 - pow((1 + Rate), -Term))),2);  
    *pVal = Payment;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputeOpeningBalance(double *pVal)  
{  
    OpeningBalance = Round(Payment / (Rate /   
        (1 - pow((1 + Rate), -Term))),2);  
    *pVal = OpeningBalance ;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputeRate(double *pVal)  
{  
    double DesiredPayment = Payment;  
  
    for (Rate = 0.001; Rate < 28.0; Rate += 0.001)  
    {  
        Payment = Round(OpeningBalance * (Rate /   
         (1 - pow((1 + Rate), -Term))),2);  
  
        if (Payment >= DesiredPayment)  
            break;  
    }  
  
    *pVal = Rate;     
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputeTerm(short *pVal)  
{  
    double DesiredPayment = Payment;  
    for (Term = 1; Term < 480 ; Term ++)  
    {  
        Payment = Round(OpeningBalance * (Rate /   
         (1 - pow((1 + Rate), -Term))),2);  
        if (Payment <= DesiredPayment)  
            break;  
    }  
    *pVal = Term;     
    return S_OK;  
}  
  
STDMETHODIMP CLoan::GetFirstPmtDistribution(double PmtAmt, double *Balance, double *PrinPortion, double *IntPortion, VARIANT_BOOL *pVal)  
{  
    *Balance = OpeningBalance;  
    GetNextPmtDistribution(PmtAmt, Balance, PrinPortion, IntPortion,   
      pVal);  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::GetNextPmtDistribution(double PmtAmt, double *Balance, double *PrinPortion, double *IntPortion, VARIANT_BOOL *pVal)  
{  
    *IntPortion = Round(*Balance * Rate, 2);  
    *PrinPortion = Round(PmtAmt - *IntPortion, 2);  
    *Balance = Round(*Balance - *PrinPortion, 2);  
  
    if (*Balance <= 0.0)  
        *pVal = FALSE;  
    else  
        *pVal = TRUE;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_RiskRating(BSTR *pVal)  
{  
    *pVal = (BSTR)RiskRating;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_RiskRating(BSTR newVal)  
{  
    RiskRating = newVal;  
    return S_OK;  
}  
static double Round(double value, short digits)   
{  
    double factor = pow(10, digits);  
    return floor(value * factor + 0.5)/factor;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca33a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca33a-108">See also</span></span>

- [<span data-ttu-id="ca33a-109">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ca33a-109">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
