---
title: "ODBC 結構描述集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="0c45a-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="0c45a-102">ODBC Schema Collections</span></span>
<span data-ttu-id="0c45a-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="0c45a-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="0c45a-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="0c45a-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="0c45a-105">Microsoft SQL Server ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="0c45a-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0c45a-106">資料表</span><span class="sxs-lookup"><span data-stu-id="0c45a-106">Tables</span></span>  
  
-   <span data-ttu-id="0c45a-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="0c45a-107">Indexes</span></span>  
  
-   <span data-ttu-id="0c45a-108">資料行</span><span class="sxs-lookup"><span data-stu-id="0c45a-108">Columns</span></span>  
  
-   <span data-ttu-id="0c45a-109">程序</span><span class="sxs-lookup"><span data-stu-id="0c45a-109">Procedures</span></span>  
  
-   <span data-ttu-id="0c45a-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c45a-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0c45a-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c45a-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0c45a-112">檢視</span><span class="sxs-lookup"><span data-stu-id="0c45a-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="0c45a-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="0c45a-113">Tables and Views</span></span>  
  
|<span data-ttu-id="0c45a-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-114">ColumnName</span></span>|<span data-ttu-id="0c45a-115">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0c45a-116">TABLE_CAT</span></span>|<span data-ttu-id="0c45a-117">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-117">String</span></span>|  
|<span data-ttu-id="0c45a-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0c45a-118">TABLE_SCHEM</span></span>|<span data-ttu-id="0c45a-119">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-119">String</span></span>|  
|<span data-ttu-id="0c45a-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-120">TABLE_NAME</span></span>|<span data-ttu-id="0c45a-121">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-121">String</span></span>|  
|<span data-ttu-id="0c45a-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-122">TABLE_TYPE</span></span>|<span data-ttu-id="0c45a-123">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-123">String</span></span>|  
|<span data-ttu-id="0c45a-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-124">REMARKS</span></span>|<span data-ttu-id="0c45a-125">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0c45a-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="0c45a-126">Indexes</span></span>  
  
|<span data-ttu-id="0c45a-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-127">ColumnName</span></span>|<span data-ttu-id="0c45a-128">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0c45a-129">TABLE_CAT</span></span>|<span data-ttu-id="0c45a-130">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-130">String</span></span>|  
|<span data-ttu-id="0c45a-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0c45a-131">TABLE_SCHEM</span></span>|<span data-ttu-id="0c45a-132">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-132">String</span></span>|  
|<span data-ttu-id="0c45a-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-133">TABLE_NAME</span></span>|<span data-ttu-id="0c45a-134">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-134">String</span></span>|  
|<span data-ttu-id="0c45a-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0c45a-135">NON_UNIQUE</span></span>|<span data-ttu-id="0c45a-136">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-136">Int16</span></span>|  
|<span data-ttu-id="0c45a-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="0c45a-138">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-138">String</span></span>|  
|<span data-ttu-id="0c45a-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-139">INDEX_NAME</span></span>|<span data-ttu-id="0c45a-140">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-140">String</span></span>|  
|<span data-ttu-id="0c45a-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-141">TYPE</span></span>|<span data-ttu-id="0c45a-142">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-142">Int16</span></span>|  
|<span data-ttu-id="0c45a-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-144">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-144">Int16</span></span>|  
|<span data-ttu-id="0c45a-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-145">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-146">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-146">String</span></span>|  
|<span data-ttu-id="0c45a-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="0c45a-147">ASC_OR_DESC</span></span>|<span data-ttu-id="0c45a-148">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-148">String</span></span>|  
|<span data-ttu-id="0c45a-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="0c45a-149">CARDINATLITY</span></span>|<span data-ttu-id="0c45a-150">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-150">Int32</span></span>|  
|<span data-ttu-id="0c45a-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="0c45a-151">PAGES</span></span>|<span data-ttu-id="0c45a-152">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-152">Int32</span></span>|  
|<span data-ttu-id="0c45a-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-153">FILTER_CONDITION</span></span>|<span data-ttu-id="0c45a-154">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-154">String</span></span>|  
|<span data-ttu-id="0c45a-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c45a-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0c45a-156">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-156">String</span></span>|  
|<span data-ttu-id="0c45a-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-158">Byte</span><span class="sxs-lookup"><span data-stu-id="0c45a-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0c45a-159">資料行</span><span class="sxs-lookup"><span data-stu-id="0c45a-159">Columns</span></span>  
  
|<span data-ttu-id="0c45a-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-160">ColumnName</span></span>|<span data-ttu-id="0c45a-161">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0c45a-162">TABLE_CAT</span></span>|<span data-ttu-id="0c45a-163">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-163">String</span></span>|  
|<span data-ttu-id="0c45a-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0c45a-164">TABLE_SCHEM</span></span>|<span data-ttu-id="0c45a-165">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-165">String</span></span>|  
|<span data-ttu-id="0c45a-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-166">TABLE_NAME</span></span>|<span data-ttu-id="0c45a-167">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-167">String</span></span>|  
|<span data-ttu-id="0c45a-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-168">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-169">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-169">String</span></span>|  
|<span data-ttu-id="0c45a-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-170">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-171">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-171">Int16</span></span>|  
|<span data-ttu-id="0c45a-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-172">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-173">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-173">String</span></span>|  
|<span data-ttu-id="0c45a-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0c45a-174">COLUMN_SIZE</span></span>|<span data-ttu-id="0c45a-175">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-175">Int32</span></span>|  
|<span data-ttu-id="0c45a-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="0c45a-177">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-177">Int32</span></span>|  
|<span data-ttu-id="0c45a-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0c45a-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0c45a-179">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-179">Int16</span></span>|  
|<span data-ttu-id="0c45a-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0c45a-181">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-181">Int16</span></span>|  
|<span data-ttu-id="0c45a-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-182">NULLABLE</span></span>|<span data-ttu-id="0c45a-183">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-183">Int16</span></span>|  
|<span data-ttu-id="0c45a-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-184">REMARKS</span></span>|<span data-ttu-id="0c45a-185">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-185">String</span></span>|  
|<span data-ttu-id="0c45a-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0c45a-186">COLUMN_DEF</span></span>|<span data-ttu-id="0c45a-187">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-187">String</span></span>|  
|<span data-ttu-id="0c45a-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-189">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-189">Int16</span></span>|  
|<span data-ttu-id="0c45a-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0c45a-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0c45a-191">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-191">Int16</span></span>|  
|<span data-ttu-id="0c45a-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0c45a-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-193">Int32</span></span>|  
|<span data-ttu-id="0c45a-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-195">Int32</span></span>|  
|<span data-ttu-id="0c45a-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-196">IS_NULLABLE</span></span>|<span data-ttu-id="0c45a-197">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-197">String</span></span>|  
|<span data-ttu-id="0c45a-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c45a-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0c45a-199">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-199">String</span></span>|  
|<span data-ttu-id="0c45a-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c45a-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0c45a-201">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-201">String</span></span>|  
|<span data-ttu-id="0c45a-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-203">Byte</span><span class="sxs-lookup"><span data-stu-id="0c45a-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0c45a-204">程序</span><span class="sxs-lookup"><span data-stu-id="0c45a-204">Procedures</span></span>  
  
|<span data-ttu-id="0c45a-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-205">ColumnName</span></span>|<span data-ttu-id="0c45a-206">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0c45a-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="0c45a-208">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-208">String</span></span>|  
|<span data-ttu-id="0c45a-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0c45a-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0c45a-210">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-210">String</span></span>|  
|<span data-ttu-id="0c45a-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-212">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-212">String</span></span>|  
|<span data-ttu-id="0c45a-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0c45a-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0c45a-214">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-214">Int32</span></span>|  
|<span data-ttu-id="0c45a-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0c45a-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0c45a-216">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-216">Int32</span></span>|  
|<span data-ttu-id="0c45a-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0c45a-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0c45a-218">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-218">Int32</span></span>|  
|<span data-ttu-id="0c45a-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-219">REMARKS</span></span>|<span data-ttu-id="0c45a-220">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-220">String</span></span>|  
|<span data-ttu-id="0c45a-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0c45a-222">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0c45a-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c45a-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0c45a-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-224">ColumnName</span></span>|<span data-ttu-id="0c45a-225">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0c45a-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="0c45a-227">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-227">String</span></span>|  
|<span data-ttu-id="0c45a-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0c45a-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0c45a-229">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-229">String</span></span>|  
|<span data-ttu-id="0c45a-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-231">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-231">String</span></span>|  
|<span data-ttu-id="0c45a-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-232">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-233">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-233">String</span></span>|  
|<span data-ttu-id="0c45a-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-234">COLUMN_TYPE</span></span>|<span data-ttu-id="0c45a-235">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-235">Int16</span></span>|  
|<span data-ttu-id="0c45a-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-236">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-237">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-237">Int16</span></span>|  
|<span data-ttu-id="0c45a-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-238">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-239">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-239">String</span></span>|  
|<span data-ttu-id="0c45a-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0c45a-240">COLUMN_SIZE</span></span>|<span data-ttu-id="0c45a-241">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-241">Int32</span></span>|  
|<span data-ttu-id="0c45a-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="0c45a-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-243">Int32</span></span>|  
|<span data-ttu-id="0c45a-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0c45a-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0c45a-245">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-245">Int16</span></span>|  
|<span data-ttu-id="0c45a-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0c45a-247">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-247">Int16</span></span>|  
|<span data-ttu-id="0c45a-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-248">NULLABLE</span></span>|<span data-ttu-id="0c45a-249">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-249">Int16</span></span>|  
|<span data-ttu-id="0c45a-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-250">REMARKS</span></span>|<span data-ttu-id="0c45a-251">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-251">String</span></span>|  
|<span data-ttu-id="0c45a-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0c45a-252">COLUMN_DEF</span></span>|<span data-ttu-id="0c45a-253">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-253">String</span></span>|  
|<span data-ttu-id="0c45a-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-255">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-255">Int16</span></span>|  
|<span data-ttu-id="0c45a-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0c45a-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0c45a-257">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-257">Int16</span></span>|  
|<span data-ttu-id="0c45a-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0c45a-259">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-259">Int32</span></span>|  
|<span data-ttu-id="0c45a-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-261">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-261">Int32</span></span>|  
|<span data-ttu-id="0c45a-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-262">IS_NULLABLE</span></span>|<span data-ttu-id="0c45a-263">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-263">String</span></span>|  
|<span data-ttu-id="0c45a-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c45a-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0c45a-265">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-265">String</span></span>|  
|<span data-ttu-id="0c45a-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c45a-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0c45a-267">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-267">String</span></span>|  
|<span data-ttu-id="0c45a-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-269">Byte</span><span class="sxs-lookup"><span data-stu-id="0c45a-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0c45a-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c45a-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0c45a-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-271">ColumnName</span></span>|<span data-ttu-id="0c45a-272">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0c45a-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="0c45a-274">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-274">String</span></span>|  
|<span data-ttu-id="0c45a-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0c45a-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0c45a-276">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-276">String</span></span>|  
|<span data-ttu-id="0c45a-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-278">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-278">String</span></span>|  
|<span data-ttu-id="0c45a-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-279">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-280">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-280">String</span></span>|  
|<span data-ttu-id="0c45a-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-281">COLUMN_TYPE</span></span>|<span data-ttu-id="0c45a-282">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-282">Int16</span></span>|  
|<span data-ttu-id="0c45a-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-283">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-284">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-284">Int16</span></span>|  
|<span data-ttu-id="0c45a-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-285">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-286">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-286">String</span></span>|  
|<span data-ttu-id="0c45a-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0c45a-287">COLUMN_SIZE</span></span>|<span data-ttu-id="0c45a-288">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-288">Int32</span></span>|  
|<span data-ttu-id="0c45a-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="0c45a-290">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-290">Int32</span></span>|  
|<span data-ttu-id="0c45a-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0c45a-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0c45a-292">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-292">Int16</span></span>|  
|<span data-ttu-id="0c45a-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0c45a-294">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-294">Int16</span></span>|  
|<span data-ttu-id="0c45a-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-295">NULLABLE</span></span>|<span data-ttu-id="0c45a-296">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-296">Int16</span></span>|  
|<span data-ttu-id="0c45a-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-297">REMARKS</span></span>|<span data-ttu-id="0c45a-298">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-298">String</span></span>|  
|<span data-ttu-id="0c45a-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0c45a-299">COLUMN_DEF</span></span>|<span data-ttu-id="0c45a-300">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-300">String</span></span>|  
|<span data-ttu-id="0c45a-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-302">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-302">Int16</span></span>|  
|<span data-ttu-id="0c45a-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0c45a-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0c45a-304">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-304">Int16</span></span>|  
|<span data-ttu-id="0c45a-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0c45a-306">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-306">Int32</span></span>|  
|<span data-ttu-id="0c45a-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-308">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-308">Int32</span></span>|  
|<span data-ttu-id="0c45a-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-309">IS_NULLABLE</span></span>|<span data-ttu-id="0c45a-310">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-310">String</span></span>|  
|<span data-ttu-id="0c45a-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0c45a-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0c45a-312">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-312">String</span></span>|  
|<span data-ttu-id="0c45a-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0c45a-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0c45a-314">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-314">String</span></span>|  
|<span data-ttu-id="0c45a-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-316">Byte</span><span class="sxs-lookup"><span data-stu-id="0c45a-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="0c45a-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="0c45a-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="0c45a-318">Microsoft SQL Server Oracle ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="0c45a-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0c45a-319">資料表</span><span class="sxs-lookup"><span data-stu-id="0c45a-319">Tables</span></span>  
  
-   <span data-ttu-id="0c45a-320">資料行</span><span class="sxs-lookup"><span data-stu-id="0c45a-320">Columns</span></span>  
  
-   <span data-ttu-id="0c45a-321">程序</span><span class="sxs-lookup"><span data-stu-id="0c45a-321">Procedures</span></span>  
  
-   <span data-ttu-id="0c45a-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c45a-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0c45a-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c45a-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0c45a-324">檢視</span><span class="sxs-lookup"><span data-stu-id="0c45a-324">Views</span></span>  
  
-   <span data-ttu-id="0c45a-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="0c45a-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="0c45a-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="0c45a-326">Tables and Views</span></span>  
  
|<span data-ttu-id="0c45a-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-327">ColumnName</span></span>|<span data-ttu-id="0c45a-328">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-330">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-330">String</span></span>|  
|<span data-ttu-id="0c45a-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-331">TABLE_OWNER</span></span>|<span data-ttu-id="0c45a-332">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-332">String</span></span>|  
|<span data-ttu-id="0c45a-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-333">TABLE_NAME</span></span>|<span data-ttu-id="0c45a-334">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-334">String</span></span>|  
|<span data-ttu-id="0c45a-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-335">TABLE_TYPE</span></span>|<span data-ttu-id="0c45a-336">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-336">String</span></span>|  
|<span data-ttu-id="0c45a-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-337">REMARKS</span></span>|<span data-ttu-id="0c45a-338">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0c45a-339">資料行</span><span class="sxs-lookup"><span data-stu-id="0c45a-339">Columns</span></span>  
  
|<span data-ttu-id="0c45a-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-340">ColumnName</span></span>|<span data-ttu-id="0c45a-341">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-343">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-343">String</span></span>|  
|<span data-ttu-id="0c45a-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-344">TABLE_OWNER</span></span>|<span data-ttu-id="0c45a-345">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-345">String</span></span>|  
|<span data-ttu-id="0c45a-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-346">TABLE_NAME</span></span>|<span data-ttu-id="0c45a-347">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-347">String</span></span>|  
|<span data-ttu-id="0c45a-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-348">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-349">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-349">String</span></span>|  
|<span data-ttu-id="0c45a-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-350">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-351">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-351">Int16</span></span>|  
|<span data-ttu-id="0c45a-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-352">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-353">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-353">String</span></span>|  
|<span data-ttu-id="0c45a-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c45a-354">PRECISION</span></span>|<span data-ttu-id="0c45a-355">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-355">Int32</span></span>|  
|<span data-ttu-id="0c45a-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-356">LENGTH</span></span>|<span data-ttu-id="0c45a-357">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-357">Int32</span></span>|  
|<span data-ttu-id="0c45a-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="0c45a-358">SCALE</span></span>|<span data-ttu-id="0c45a-359">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-359">Int16</span></span>|  
|<span data-ttu-id="0c45a-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-360">RADIX</span></span>|<span data-ttu-id="0c45a-361">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-361">Int16</span></span>|  
|<span data-ttu-id="0c45a-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-362">NULLABLE</span></span>|<span data-ttu-id="0c45a-363">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-363">Int16</span></span>|  
|<span data-ttu-id="0c45a-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-364">REMARKS</span></span>|<span data-ttu-id="0c45a-365">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-365">String</span></span>|  
|<span data-ttu-id="0c45a-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-367">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0c45a-368">程序</span><span class="sxs-lookup"><span data-stu-id="0c45a-368">Procedures</span></span>  
  
|<span data-ttu-id="0c45a-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-369">ColumnName</span></span>|<span data-ttu-id="0c45a-370">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-372">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-372">String</span></span>|  
|<span data-ttu-id="0c45a-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0c45a-374">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-374">String</span></span>|  
|<span data-ttu-id="0c45a-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-376">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-376">String</span></span>|  
|<span data-ttu-id="0c45a-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0c45a-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0c45a-378">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-378">Int16</span></span>|  
|<span data-ttu-id="0c45a-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0c45a-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0c45a-380">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-380">Int16</span></span>|  
|<span data-ttu-id="0c45a-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0c45a-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0c45a-382">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-382">Int16</span></span>|  
|<span data-ttu-id="0c45a-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-383">REMARKS</span></span>|<span data-ttu-id="0c45a-384">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-384">String</span></span>|  
|<span data-ttu-id="0c45a-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0c45a-386">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0c45a-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c45a-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0c45a-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-388">ColumnName</span></span>|<span data-ttu-id="0c45a-389">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-391">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-391">String</span></span>|  
|<span data-ttu-id="0c45a-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0c45a-393">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-393">String</span></span>|  
|<span data-ttu-id="0c45a-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-395">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-395">String</span></span>|  
|<span data-ttu-id="0c45a-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-396">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-397">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-397">String</span></span>|  
|<span data-ttu-id="0c45a-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-398">COLUMN_TYPE</span></span>|<span data-ttu-id="0c45a-399">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-399">Int16</span></span>|  
|<span data-ttu-id="0c45a-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-400">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-401">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-401">Int16</span></span>|  
|<span data-ttu-id="0c45a-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-402">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-403">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-403">String</span></span>|  
|<span data-ttu-id="0c45a-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c45a-404">PRECISION</span></span>|<span data-ttu-id="0c45a-405">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-405">Int32</span></span>|  
|<span data-ttu-id="0c45a-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-406">LENGTH</span></span>|<span data-ttu-id="0c45a-407">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-407">Int32</span></span>|  
|<span data-ttu-id="0c45a-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="0c45a-408">SCALE</span></span>|<span data-ttu-id="0c45a-409">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-409">Int16</span></span>|  
|<span data-ttu-id="0c45a-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-410">RADIX</span></span>|<span data-ttu-id="0c45a-411">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-411">Int16</span></span>|  
|<span data-ttu-id="0c45a-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-412">NULLABLE</span></span>|<span data-ttu-id="0c45a-413">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-413">Int16</span></span>|  
|<span data-ttu-id="0c45a-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-414">REMARKS</span></span>|<span data-ttu-id="0c45a-415">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-415">String</span></span>|  
|<span data-ttu-id="0c45a-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="0c45a-416">OVERLOAD</span></span>|<span data-ttu-id="0c45a-417">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-417">Int32</span></span>|  
|<span data-ttu-id="0c45a-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-419">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="0c45a-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="0c45a-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="0c45a-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="0c45a-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0c45a-422">資料表</span><span class="sxs-lookup"><span data-stu-id="0c45a-422">Tables</span></span>  
  
-   <span data-ttu-id="0c45a-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="0c45a-423">Indexes</span></span>  
  
-   <span data-ttu-id="0c45a-424">資料行</span><span class="sxs-lookup"><span data-stu-id="0c45a-424">Columns</span></span>  
  
-   <span data-ttu-id="0c45a-425">程序</span><span class="sxs-lookup"><span data-stu-id="0c45a-425">Procedures</span></span>  
  
-   <span data-ttu-id="0c45a-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c45a-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0c45a-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c45a-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0c45a-428">檢視</span><span class="sxs-lookup"><span data-stu-id="0c45a-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="0c45a-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="0c45a-429">Tables and Views</span></span>  
  
|<span data-ttu-id="0c45a-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-430">ColumnName</span></span>|<span data-ttu-id="0c45a-431">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-433">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-433">String</span></span>|  
|<span data-ttu-id="0c45a-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-434">TABLE_OWNER</span></span>|<span data-ttu-id="0c45a-435">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-435">String</span></span>|  
|<span data-ttu-id="0c45a-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-436">TABLE_NAME</span></span>|<span data-ttu-id="0c45a-437">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-437">String</span></span>|  
|<span data-ttu-id="0c45a-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-438">TABLE_TYPE</span></span>|<span data-ttu-id="0c45a-439">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-439">String</span></span>|  
|<span data-ttu-id="0c45a-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-440">REMARKS</span></span>|<span data-ttu-id="0c45a-441">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0c45a-442">資料行</span><span class="sxs-lookup"><span data-stu-id="0c45a-442">Columns</span></span>  
  
|<span data-ttu-id="0c45a-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-443">ColumnName</span></span>|<span data-ttu-id="0c45a-444">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-446">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-446">String</span></span>|  
|<span data-ttu-id="0c45a-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-447">TABLE_OWNER</span></span>|<span data-ttu-id="0c45a-448">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-448">String</span></span>|  
|<span data-ttu-id="0c45a-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-449">TABLE_NAME</span></span>|<span data-ttu-id="0c45a-450">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-450">String</span></span>|  
|<span data-ttu-id="0c45a-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-451">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-452">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-452">String</span></span>|  
|<span data-ttu-id="0c45a-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-453">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-454">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-454">Int16</span></span>|  
|<span data-ttu-id="0c45a-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-455">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-456">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-456">String</span></span>|  
|<span data-ttu-id="0c45a-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c45a-457">PRECISION</span></span>|<span data-ttu-id="0c45a-458">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-458">Int32</span></span>|  
|<span data-ttu-id="0c45a-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-459">LENGTH</span></span>|<span data-ttu-id="0c45a-460">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-460">Int32</span></span>|  
|<span data-ttu-id="0c45a-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="0c45a-461">SCALE</span></span>|<span data-ttu-id="0c45a-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-462">Int16</span></span>|  
|<span data-ttu-id="0c45a-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-463">RADIX</span></span>|<span data-ttu-id="0c45a-464">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-464">Int16</span></span>|  
|<span data-ttu-id="0c45a-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-465">NULLABLE</span></span>|<span data-ttu-id="0c45a-466">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-466">Int16</span></span>|  
|<span data-ttu-id="0c45a-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-467">REMARKS</span></span>|<span data-ttu-id="0c45a-468">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-468">String</span></span>|  
|<span data-ttu-id="0c45a-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-470">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0c45a-471">程序</span><span class="sxs-lookup"><span data-stu-id="0c45a-471">Procedures</span></span>  
  
|<span data-ttu-id="0c45a-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-472">ColumnName</span></span>|<span data-ttu-id="0c45a-473">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-475">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-475">String</span></span>|  
|<span data-ttu-id="0c45a-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0c45a-477">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-477">String</span></span>|  
|<span data-ttu-id="0c45a-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-479">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-479">String</span></span>|  
|<span data-ttu-id="0c45a-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0c45a-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0c45a-481">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-481">Int16</span></span>|  
|<span data-ttu-id="0c45a-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0c45a-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0c45a-483">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-483">Int16</span></span>|  
|<span data-ttu-id="0c45a-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0c45a-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0c45a-485">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-485">Int16</span></span>|  
|<span data-ttu-id="0c45a-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-486">REMARKS</span></span>|<span data-ttu-id="0c45a-487">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-487">String</span></span>|  
|<span data-ttu-id="0c45a-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0c45a-489">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0c45a-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0c45a-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0c45a-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-491">ColumnName</span></span>|<span data-ttu-id="0c45a-492">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0c45a-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0c45a-494">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-494">String</span></span>|  
|<span data-ttu-id="0c45a-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c45a-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0c45a-496">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-496">String</span></span>|  
|<span data-ttu-id="0c45a-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-498">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-498">String</span></span>|  
|<span data-ttu-id="0c45a-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-499">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-500">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-500">String</span></span>|  
|<span data-ttu-id="0c45a-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-501">COLUMN_TYPE</span></span>|<span data-ttu-id="0c45a-502">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-502">Int16</span></span>|  
|<span data-ttu-id="0c45a-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-503">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-504">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-504">Int16</span></span>|  
|<span data-ttu-id="0c45a-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-505">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-506">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-506">String</span></span>|  
|<span data-ttu-id="0c45a-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="0c45a-507">PRECISION</span></span>|<span data-ttu-id="0c45a-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-508">Int32</span></span>|  
|<span data-ttu-id="0c45a-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-509">LENGTH</span></span>|<span data-ttu-id="0c45a-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-510">Int32</span></span>|  
|<span data-ttu-id="0c45a-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="0c45a-511">SCALE</span></span>|<span data-ttu-id="0c45a-512">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-512">Int16</span></span>|  
|<span data-ttu-id="0c45a-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-513">RADIX</span></span>|<span data-ttu-id="0c45a-514">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-514">Int16</span></span>|  
|<span data-ttu-id="0c45a-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-515">NULLABLE</span></span>|<span data-ttu-id="0c45a-516">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-516">Int16</span></span>|  
|<span data-ttu-id="0c45a-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-517">REMARKS</span></span>|<span data-ttu-id="0c45a-518">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-518">String</span></span>|  
|<span data-ttu-id="0c45a-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="0c45a-519">OVERLOAD</span></span>|<span data-ttu-id="0c45a-520">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-520">Int32</span></span>|  
|<span data-ttu-id="0c45a-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-522">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0c45a-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0c45a-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0c45a-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0c45a-524">ColumnName</span></span>|<span data-ttu-id="0c45a-525">DataType</span><span class="sxs-lookup"><span data-stu-id="0c45a-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0c45a-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0c45a-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="0c45a-527">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-527">String</span></span>|  
|<span data-ttu-id="0c45a-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0c45a-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0c45a-529">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-529">String</span></span>|  
|<span data-ttu-id="0c45a-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="0c45a-531">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-531">String</span></span>|  
|<span data-ttu-id="0c45a-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-532">COLUMN_NAME</span></span>|<span data-ttu-id="0c45a-533">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-533">String</span></span>|  
|<span data-ttu-id="0c45a-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-534">COLUMN_TYPE</span></span>|<span data-ttu-id="0c45a-535">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-535">Int16</span></span>|  
|<span data-ttu-id="0c45a-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-536">DATA_TYPE</span></span>|<span data-ttu-id="0c45a-537">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-537">Int16</span></span>|  
|<span data-ttu-id="0c45a-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0c45a-538">TYPE_NAME</span></span>|<span data-ttu-id="0c45a-539">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-539">String</span></span>|  
|<span data-ttu-id="0c45a-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0c45a-540">COLUMN_SIZE</span></span>|<span data-ttu-id="0c45a-541">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-541">Int32</span></span>|  
|<span data-ttu-id="0c45a-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="0c45a-543">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-543">Int32</span></span>|  
|<span data-ttu-id="0c45a-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0c45a-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0c45a-545">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-545">Int16</span></span>|  
|<span data-ttu-id="0c45a-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0c45a-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0c45a-547">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-547">Int16</span></span>|  
|<span data-ttu-id="0c45a-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-548">NULLABLE</span></span>|<span data-ttu-id="0c45a-549">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-549">Int16</span></span>|  
|<span data-ttu-id="0c45a-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0c45a-550">REMARKS</span></span>|<span data-ttu-id="0c45a-551">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-551">String</span></span>|  
|<span data-ttu-id="0c45a-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0c45a-552">COLUMN_DEF</span></span>|<span data-ttu-id="0c45a-553">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-553">String</span></span>|  
|<span data-ttu-id="0c45a-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0c45a-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0c45a-555">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-555">Int16</span></span>|  
|<span data-ttu-id="0c45a-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0c45a-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0c45a-557">Int16</span><span class="sxs-lookup"><span data-stu-id="0c45a-557">Int16</span></span>|  
|<span data-ttu-id="0c45a-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0c45a-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0c45a-559">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-559">Int32</span></span>|  
|<span data-ttu-id="0c45a-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0c45a-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="0c45a-561">Int32</span><span class="sxs-lookup"><span data-stu-id="0c45a-561">Int32</span></span>|  
|<span data-ttu-id="0c45a-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0c45a-562">IS_NULLABLE</span></span>|<span data-ttu-id="0c45a-563">String</span><span class="sxs-lookup"><span data-stu-id="0c45a-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c45a-564">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c45a-564">See Also</span></span>  
 [<span data-ttu-id="0c45a-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0c45a-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
