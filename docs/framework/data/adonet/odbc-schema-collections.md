---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479976"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="db12e-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="db12e-102">ODBC Schema Collections</span></span>
<span data-ttu-id="db12e-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="db12e-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="db12e-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="db12e-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="db12e-105">Microsoft SQL Server ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="db12e-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="db12e-106">資料表</span><span class="sxs-lookup"><span data-stu-id="db12e-106">Tables</span></span>  
  
-   <span data-ttu-id="db12e-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="db12e-107">Indexes</span></span>  
  
-   <span data-ttu-id="db12e-108">資料行</span><span class="sxs-lookup"><span data-stu-id="db12e-108">Columns</span></span>  
  
-   <span data-ttu-id="db12e-109">程序</span><span class="sxs-lookup"><span data-stu-id="db12e-109">Procedures</span></span>  
  
-   <span data-ttu-id="db12e-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db12e-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="db12e-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db12e-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="db12e-112">檢視</span><span class="sxs-lookup"><span data-stu-id="db12e-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="db12e-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="db12e-113">Tables and Views</span></span>  
  
|<span data-ttu-id="db12e-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-114">ColumnName</span></span>|<span data-ttu-id="db12e-115">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="db12e-116">TABLE_CAT</span></span>|<span data-ttu-id="db12e-117">String</span><span class="sxs-lookup"><span data-stu-id="db12e-117">String</span></span>|  
|<span data-ttu-id="db12e-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="db12e-118">TABLE_SCHEM</span></span>|<span data-ttu-id="db12e-119">String</span><span class="sxs-lookup"><span data-stu-id="db12e-119">String</span></span>|  
|<span data-ttu-id="db12e-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-120">TABLE_NAME</span></span>|<span data-ttu-id="db12e-121">String</span><span class="sxs-lookup"><span data-stu-id="db12e-121">String</span></span>|  
|<span data-ttu-id="db12e-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-122">TABLE_TYPE</span></span>|<span data-ttu-id="db12e-123">String</span><span class="sxs-lookup"><span data-stu-id="db12e-123">String</span></span>|  
|<span data-ttu-id="db12e-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-124">REMARKS</span></span>|<span data-ttu-id="db12e-125">String</span><span class="sxs-lookup"><span data-stu-id="db12e-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="db12e-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="db12e-126">Indexes</span></span>  
  
|<span data-ttu-id="db12e-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-127">ColumnName</span></span>|<span data-ttu-id="db12e-128">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="db12e-129">TABLE_CAT</span></span>|<span data-ttu-id="db12e-130">String</span><span class="sxs-lookup"><span data-stu-id="db12e-130">String</span></span>|  
|<span data-ttu-id="db12e-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="db12e-131">TABLE_SCHEM</span></span>|<span data-ttu-id="db12e-132">String</span><span class="sxs-lookup"><span data-stu-id="db12e-132">String</span></span>|  
|<span data-ttu-id="db12e-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-133">TABLE_NAME</span></span>|<span data-ttu-id="db12e-134">String</span><span class="sxs-lookup"><span data-stu-id="db12e-134">String</span></span>|  
|<span data-ttu-id="db12e-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="db12e-135">NON_UNIQUE</span></span>|<span data-ttu-id="db12e-136">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-136">Int16</span></span>|  
|<span data-ttu-id="db12e-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="db12e-138">String</span><span class="sxs-lookup"><span data-stu-id="db12e-138">String</span></span>|  
|<span data-ttu-id="db12e-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-139">INDEX_NAME</span></span>|<span data-ttu-id="db12e-140">String</span><span class="sxs-lookup"><span data-stu-id="db12e-140">String</span></span>|  
|<span data-ttu-id="db12e-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-141">TYPE</span></span>|<span data-ttu-id="db12e-142">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-142">Int16</span></span>|  
|<span data-ttu-id="db12e-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-144">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-144">Int16</span></span>|  
|<span data-ttu-id="db12e-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-145">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-146">String</span><span class="sxs-lookup"><span data-stu-id="db12e-146">String</span></span>|  
|<span data-ttu-id="db12e-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="db12e-147">ASC_OR_DESC</span></span>|<span data-ttu-id="db12e-148">String</span><span class="sxs-lookup"><span data-stu-id="db12e-148">String</span></span>|  
|<span data-ttu-id="db12e-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="db12e-149">CARDINATLITY</span></span>|<span data-ttu-id="db12e-150">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-150">Int32</span></span>|  
|<span data-ttu-id="db12e-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="db12e-151">PAGES</span></span>|<span data-ttu-id="db12e-152">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-152">Int32</span></span>|  
|<span data-ttu-id="db12e-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="db12e-153">FILTER_CONDITION</span></span>|<span data-ttu-id="db12e-154">String</span><span class="sxs-lookup"><span data-stu-id="db12e-154">String</span></span>|  
|<span data-ttu-id="db12e-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db12e-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="db12e-156">String</span><span class="sxs-lookup"><span data-stu-id="db12e-156">String</span></span>|  
|<span data-ttu-id="db12e-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="db12e-158">Byte</span><span class="sxs-lookup"><span data-stu-id="db12e-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="db12e-159">資料行</span><span class="sxs-lookup"><span data-stu-id="db12e-159">Columns</span></span>  
  
|<span data-ttu-id="db12e-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-160">ColumnName</span></span>|<span data-ttu-id="db12e-161">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="db12e-162">TABLE_CAT</span></span>|<span data-ttu-id="db12e-163">String</span><span class="sxs-lookup"><span data-stu-id="db12e-163">String</span></span>|  
|<span data-ttu-id="db12e-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="db12e-164">TABLE_SCHEM</span></span>|<span data-ttu-id="db12e-165">String</span><span class="sxs-lookup"><span data-stu-id="db12e-165">String</span></span>|  
|<span data-ttu-id="db12e-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-166">TABLE_NAME</span></span>|<span data-ttu-id="db12e-167">String</span><span class="sxs-lookup"><span data-stu-id="db12e-167">String</span></span>|  
|<span data-ttu-id="db12e-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-168">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-169">String</span><span class="sxs-lookup"><span data-stu-id="db12e-169">String</span></span>|  
|<span data-ttu-id="db12e-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-170">DATA_TYPE</span></span>|<span data-ttu-id="db12e-171">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-171">Int16</span></span>|  
|<span data-ttu-id="db12e-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-172">TYPE_NAME</span></span>|<span data-ttu-id="db12e-173">String</span><span class="sxs-lookup"><span data-stu-id="db12e-173">String</span></span>|  
|<span data-ttu-id="db12e-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="db12e-174">COLUMN_SIZE</span></span>|<span data-ttu-id="db12e-175">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-175">Int32</span></span>|  
|<span data-ttu-id="db12e-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="db12e-177">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-177">Int32</span></span>|  
|<span data-ttu-id="db12e-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="db12e-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="db12e-179">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-179">Int16</span></span>|  
|<span data-ttu-id="db12e-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="db12e-181">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-181">Int16</span></span>|  
|<span data-ttu-id="db12e-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-182">NULLABLE</span></span>|<span data-ttu-id="db12e-183">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-183">Int16</span></span>|  
|<span data-ttu-id="db12e-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-184">REMARKS</span></span>|<span data-ttu-id="db12e-185">String</span><span class="sxs-lookup"><span data-stu-id="db12e-185">String</span></span>|  
|<span data-ttu-id="db12e-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="db12e-186">COLUMN_DEF</span></span>|<span data-ttu-id="db12e-187">String</span><span class="sxs-lookup"><span data-stu-id="db12e-187">String</span></span>|  
|<span data-ttu-id="db12e-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="db12e-189">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-189">Int16</span></span>|  
|<span data-ttu-id="db12e-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="db12e-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="db12e-191">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-191">Int16</span></span>|  
|<span data-ttu-id="db12e-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="db12e-193">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-193">Int32</span></span>|  
|<span data-ttu-id="db12e-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-195">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-195">Int32</span></span>|  
|<span data-ttu-id="db12e-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-196">IS_NULLABLE</span></span>|<span data-ttu-id="db12e-197">String</span><span class="sxs-lookup"><span data-stu-id="db12e-197">String</span></span>|  
|<span data-ttu-id="db12e-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db12e-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="db12e-199">String</span><span class="sxs-lookup"><span data-stu-id="db12e-199">String</span></span>|  
|<span data-ttu-id="db12e-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db12e-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="db12e-201">String</span><span class="sxs-lookup"><span data-stu-id="db12e-201">String</span></span>|  
|<span data-ttu-id="db12e-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="db12e-203">Byte</span><span class="sxs-lookup"><span data-stu-id="db12e-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="db12e-204">程序</span><span class="sxs-lookup"><span data-stu-id="db12e-204">Procedures</span></span>  
  
|<span data-ttu-id="db12e-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-205">ColumnName</span></span>|<span data-ttu-id="db12e-206">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="db12e-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="db12e-208">String</span><span class="sxs-lookup"><span data-stu-id="db12e-208">String</span></span>|  
|<span data-ttu-id="db12e-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="db12e-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="db12e-210">String</span><span class="sxs-lookup"><span data-stu-id="db12e-210">String</span></span>|  
|<span data-ttu-id="db12e-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-212">String</span><span class="sxs-lookup"><span data-stu-id="db12e-212">String</span></span>|  
|<span data-ttu-id="db12e-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="db12e-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="db12e-214">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-214">Int32</span></span>|  
|<span data-ttu-id="db12e-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="db12e-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="db12e-216">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-216">Int32</span></span>|  
|<span data-ttu-id="db12e-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="db12e-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="db12e-218">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-218">Int32</span></span>|  
|<span data-ttu-id="db12e-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-219">REMARKS</span></span>|<span data-ttu-id="db12e-220">String</span><span class="sxs-lookup"><span data-stu-id="db12e-220">String</span></span>|  
|<span data-ttu-id="db12e-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="db12e-222">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="db12e-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db12e-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="db12e-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-224">ColumnName</span></span>|<span data-ttu-id="db12e-225">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="db12e-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="db12e-227">String</span><span class="sxs-lookup"><span data-stu-id="db12e-227">String</span></span>|  
|<span data-ttu-id="db12e-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="db12e-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="db12e-229">String</span><span class="sxs-lookup"><span data-stu-id="db12e-229">String</span></span>|  
|<span data-ttu-id="db12e-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-231">String</span><span class="sxs-lookup"><span data-stu-id="db12e-231">String</span></span>|  
|<span data-ttu-id="db12e-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-232">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-233">String</span><span class="sxs-lookup"><span data-stu-id="db12e-233">String</span></span>|  
|<span data-ttu-id="db12e-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-234">COLUMN_TYPE</span></span>|<span data-ttu-id="db12e-235">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-235">Int16</span></span>|  
|<span data-ttu-id="db12e-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-236">DATA_TYPE</span></span>|<span data-ttu-id="db12e-237">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-237">Int16</span></span>|  
|<span data-ttu-id="db12e-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-238">TYPE_NAME</span></span>|<span data-ttu-id="db12e-239">String</span><span class="sxs-lookup"><span data-stu-id="db12e-239">String</span></span>|  
|<span data-ttu-id="db12e-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="db12e-240">COLUMN_SIZE</span></span>|<span data-ttu-id="db12e-241">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-241">Int32</span></span>|  
|<span data-ttu-id="db12e-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="db12e-243">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-243">Int32</span></span>|  
|<span data-ttu-id="db12e-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="db12e-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="db12e-245">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-245">Int16</span></span>|  
|<span data-ttu-id="db12e-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="db12e-247">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-247">Int16</span></span>|  
|<span data-ttu-id="db12e-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-248">NULLABLE</span></span>|<span data-ttu-id="db12e-249">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-249">Int16</span></span>|  
|<span data-ttu-id="db12e-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-250">REMARKS</span></span>|<span data-ttu-id="db12e-251">String</span><span class="sxs-lookup"><span data-stu-id="db12e-251">String</span></span>|  
|<span data-ttu-id="db12e-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="db12e-252">COLUMN_DEF</span></span>|<span data-ttu-id="db12e-253">String</span><span class="sxs-lookup"><span data-stu-id="db12e-253">String</span></span>|  
|<span data-ttu-id="db12e-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="db12e-255">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-255">Int16</span></span>|  
|<span data-ttu-id="db12e-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="db12e-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="db12e-257">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-257">Int16</span></span>|  
|<span data-ttu-id="db12e-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="db12e-259">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-259">Int32</span></span>|  
|<span data-ttu-id="db12e-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-261">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-261">Int32</span></span>|  
|<span data-ttu-id="db12e-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-262">IS_NULLABLE</span></span>|<span data-ttu-id="db12e-263">String</span><span class="sxs-lookup"><span data-stu-id="db12e-263">String</span></span>|  
|<span data-ttu-id="db12e-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db12e-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="db12e-265">String</span><span class="sxs-lookup"><span data-stu-id="db12e-265">String</span></span>|  
|<span data-ttu-id="db12e-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db12e-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="db12e-267">String</span><span class="sxs-lookup"><span data-stu-id="db12e-267">String</span></span>|  
|<span data-ttu-id="db12e-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="db12e-269">Byte</span><span class="sxs-lookup"><span data-stu-id="db12e-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="db12e-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db12e-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="db12e-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-271">ColumnName</span></span>|<span data-ttu-id="db12e-272">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="db12e-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="db12e-274">String</span><span class="sxs-lookup"><span data-stu-id="db12e-274">String</span></span>|  
|<span data-ttu-id="db12e-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="db12e-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="db12e-276">String</span><span class="sxs-lookup"><span data-stu-id="db12e-276">String</span></span>|  
|<span data-ttu-id="db12e-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-278">String</span><span class="sxs-lookup"><span data-stu-id="db12e-278">String</span></span>|  
|<span data-ttu-id="db12e-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-279">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-280">String</span><span class="sxs-lookup"><span data-stu-id="db12e-280">String</span></span>|  
|<span data-ttu-id="db12e-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-281">COLUMN_TYPE</span></span>|<span data-ttu-id="db12e-282">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-282">Int16</span></span>|  
|<span data-ttu-id="db12e-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-283">DATA_TYPE</span></span>|<span data-ttu-id="db12e-284">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-284">Int16</span></span>|  
|<span data-ttu-id="db12e-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-285">TYPE_NAME</span></span>|<span data-ttu-id="db12e-286">String</span><span class="sxs-lookup"><span data-stu-id="db12e-286">String</span></span>|  
|<span data-ttu-id="db12e-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="db12e-287">COLUMN_SIZE</span></span>|<span data-ttu-id="db12e-288">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-288">Int32</span></span>|  
|<span data-ttu-id="db12e-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="db12e-290">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-290">Int32</span></span>|  
|<span data-ttu-id="db12e-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="db12e-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="db12e-292">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-292">Int16</span></span>|  
|<span data-ttu-id="db12e-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="db12e-294">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-294">Int16</span></span>|  
|<span data-ttu-id="db12e-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-295">NULLABLE</span></span>|<span data-ttu-id="db12e-296">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-296">Int16</span></span>|  
|<span data-ttu-id="db12e-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-297">REMARKS</span></span>|<span data-ttu-id="db12e-298">String</span><span class="sxs-lookup"><span data-stu-id="db12e-298">String</span></span>|  
|<span data-ttu-id="db12e-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="db12e-299">COLUMN_DEF</span></span>|<span data-ttu-id="db12e-300">String</span><span class="sxs-lookup"><span data-stu-id="db12e-300">String</span></span>|  
|<span data-ttu-id="db12e-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="db12e-302">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-302">Int16</span></span>|  
|<span data-ttu-id="db12e-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="db12e-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="db12e-304">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-304">Int16</span></span>|  
|<span data-ttu-id="db12e-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="db12e-306">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-306">Int32</span></span>|  
|<span data-ttu-id="db12e-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-308">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-308">Int32</span></span>|  
|<span data-ttu-id="db12e-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-309">IS_NULLABLE</span></span>|<span data-ttu-id="db12e-310">String</span><span class="sxs-lookup"><span data-stu-id="db12e-310">String</span></span>|  
|<span data-ttu-id="db12e-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="db12e-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="db12e-312">String</span><span class="sxs-lookup"><span data-stu-id="db12e-312">String</span></span>|  
|<span data-ttu-id="db12e-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="db12e-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="db12e-314">String</span><span class="sxs-lookup"><span data-stu-id="db12e-314">String</span></span>|  
|<span data-ttu-id="db12e-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="db12e-316">Byte</span><span class="sxs-lookup"><span data-stu-id="db12e-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="db12e-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="db12e-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="db12e-318">Microsoft SQL Server Oracle ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="db12e-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="db12e-319">資料表</span><span class="sxs-lookup"><span data-stu-id="db12e-319">Tables</span></span>  
  
-   <span data-ttu-id="db12e-320">資料行</span><span class="sxs-lookup"><span data-stu-id="db12e-320">Columns</span></span>  
  
-   <span data-ttu-id="db12e-321">程序</span><span class="sxs-lookup"><span data-stu-id="db12e-321">Procedures</span></span>  
  
-   <span data-ttu-id="db12e-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db12e-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="db12e-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db12e-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="db12e-324">檢視</span><span class="sxs-lookup"><span data-stu-id="db12e-324">Views</span></span>  
  
-   <span data-ttu-id="db12e-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="db12e-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="db12e-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="db12e-326">Tables and Views</span></span>  
  
|<span data-ttu-id="db12e-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-327">ColumnName</span></span>|<span data-ttu-id="db12e-328">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="db12e-330">String</span><span class="sxs-lookup"><span data-stu-id="db12e-330">String</span></span>|  
|<span data-ttu-id="db12e-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-331">TABLE_OWNER</span></span>|<span data-ttu-id="db12e-332">String</span><span class="sxs-lookup"><span data-stu-id="db12e-332">String</span></span>|  
|<span data-ttu-id="db12e-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-333">TABLE_NAME</span></span>|<span data-ttu-id="db12e-334">String</span><span class="sxs-lookup"><span data-stu-id="db12e-334">String</span></span>|  
|<span data-ttu-id="db12e-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-335">TABLE_TYPE</span></span>|<span data-ttu-id="db12e-336">String</span><span class="sxs-lookup"><span data-stu-id="db12e-336">String</span></span>|  
|<span data-ttu-id="db12e-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-337">REMARKS</span></span>|<span data-ttu-id="db12e-338">String</span><span class="sxs-lookup"><span data-stu-id="db12e-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="db12e-339">資料行</span><span class="sxs-lookup"><span data-stu-id="db12e-339">Columns</span></span>  
  
|<span data-ttu-id="db12e-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-340">ColumnName</span></span>|<span data-ttu-id="db12e-341">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="db12e-343">String</span><span class="sxs-lookup"><span data-stu-id="db12e-343">String</span></span>|  
|<span data-ttu-id="db12e-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-344">TABLE_OWNER</span></span>|<span data-ttu-id="db12e-345">String</span><span class="sxs-lookup"><span data-stu-id="db12e-345">String</span></span>|  
|<span data-ttu-id="db12e-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-346">TABLE_NAME</span></span>|<span data-ttu-id="db12e-347">String</span><span class="sxs-lookup"><span data-stu-id="db12e-347">String</span></span>|  
|<span data-ttu-id="db12e-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-348">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-349">String</span><span class="sxs-lookup"><span data-stu-id="db12e-349">String</span></span>|  
|<span data-ttu-id="db12e-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-350">DATA_TYPE</span></span>|<span data-ttu-id="db12e-351">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-351">Int16</span></span>|  
|<span data-ttu-id="db12e-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-352">TYPE_NAME</span></span>|<span data-ttu-id="db12e-353">String</span><span class="sxs-lookup"><span data-stu-id="db12e-353">String</span></span>|  
|<span data-ttu-id="db12e-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="db12e-354">PRECISION</span></span>|<span data-ttu-id="db12e-355">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-355">Int32</span></span>|  
|<span data-ttu-id="db12e-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-356">LENGTH</span></span>|<span data-ttu-id="db12e-357">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-357">Int32</span></span>|  
|<span data-ttu-id="db12e-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="db12e-358">SCALE</span></span>|<span data-ttu-id="db12e-359">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-359">Int16</span></span>|  
|<span data-ttu-id="db12e-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-360">RADIX</span></span>|<span data-ttu-id="db12e-361">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-361">Int16</span></span>|  
|<span data-ttu-id="db12e-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-362">NULLABLE</span></span>|<span data-ttu-id="db12e-363">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-363">Int16</span></span>|  
|<span data-ttu-id="db12e-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-364">REMARKS</span></span>|<span data-ttu-id="db12e-365">String</span><span class="sxs-lookup"><span data-stu-id="db12e-365">String</span></span>|  
|<span data-ttu-id="db12e-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-367">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="db12e-368">程序</span><span class="sxs-lookup"><span data-stu-id="db12e-368">Procedures</span></span>  
  
|<span data-ttu-id="db12e-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-369">ColumnName</span></span>|<span data-ttu-id="db12e-370">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="db12e-372">String</span><span class="sxs-lookup"><span data-stu-id="db12e-372">String</span></span>|  
|<span data-ttu-id="db12e-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="db12e-374">String</span><span class="sxs-lookup"><span data-stu-id="db12e-374">String</span></span>|  
|<span data-ttu-id="db12e-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-376">String</span><span class="sxs-lookup"><span data-stu-id="db12e-376">String</span></span>|  
|<span data-ttu-id="db12e-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="db12e-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="db12e-378">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-378">Int16</span></span>|  
|<span data-ttu-id="db12e-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="db12e-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="db12e-380">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-380">Int16</span></span>|  
|<span data-ttu-id="db12e-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="db12e-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="db12e-382">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-382">Int16</span></span>|  
|<span data-ttu-id="db12e-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-383">REMARKS</span></span>|<span data-ttu-id="db12e-384">String</span><span class="sxs-lookup"><span data-stu-id="db12e-384">String</span></span>|  
|<span data-ttu-id="db12e-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="db12e-386">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="db12e-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db12e-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="db12e-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-388">ColumnName</span></span>|<span data-ttu-id="db12e-389">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="db12e-391">String</span><span class="sxs-lookup"><span data-stu-id="db12e-391">String</span></span>|  
|<span data-ttu-id="db12e-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="db12e-393">String</span><span class="sxs-lookup"><span data-stu-id="db12e-393">String</span></span>|  
|<span data-ttu-id="db12e-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-395">String</span><span class="sxs-lookup"><span data-stu-id="db12e-395">String</span></span>|  
|<span data-ttu-id="db12e-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-396">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-397">String</span><span class="sxs-lookup"><span data-stu-id="db12e-397">String</span></span>|  
|<span data-ttu-id="db12e-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-398">COLUMN_TYPE</span></span>|<span data-ttu-id="db12e-399">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-399">Int16</span></span>|  
|<span data-ttu-id="db12e-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-400">DATA_TYPE</span></span>|<span data-ttu-id="db12e-401">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-401">Int16</span></span>|  
|<span data-ttu-id="db12e-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-402">TYPE_NAME</span></span>|<span data-ttu-id="db12e-403">String</span><span class="sxs-lookup"><span data-stu-id="db12e-403">String</span></span>|  
|<span data-ttu-id="db12e-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="db12e-404">PRECISION</span></span>|<span data-ttu-id="db12e-405">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-405">Int32</span></span>|  
|<span data-ttu-id="db12e-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-406">LENGTH</span></span>|<span data-ttu-id="db12e-407">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-407">Int32</span></span>|  
|<span data-ttu-id="db12e-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="db12e-408">SCALE</span></span>|<span data-ttu-id="db12e-409">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-409">Int16</span></span>|  
|<span data-ttu-id="db12e-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-410">RADIX</span></span>|<span data-ttu-id="db12e-411">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-411">Int16</span></span>|  
|<span data-ttu-id="db12e-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-412">NULLABLE</span></span>|<span data-ttu-id="db12e-413">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-413">Int16</span></span>|  
|<span data-ttu-id="db12e-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-414">REMARKS</span></span>|<span data-ttu-id="db12e-415">String</span><span class="sxs-lookup"><span data-stu-id="db12e-415">String</span></span>|  
|<span data-ttu-id="db12e-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="db12e-416">OVERLOAD</span></span>|<span data-ttu-id="db12e-417">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-417">Int32</span></span>|  
|<span data-ttu-id="db12e-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-419">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="db12e-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="db12e-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="db12e-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="db12e-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="db12e-422">資料表</span><span class="sxs-lookup"><span data-stu-id="db12e-422">Tables</span></span>  
  
-   <span data-ttu-id="db12e-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="db12e-423">Indexes</span></span>  
  
-   <span data-ttu-id="db12e-424">資料行</span><span class="sxs-lookup"><span data-stu-id="db12e-424">Columns</span></span>  
  
-   <span data-ttu-id="db12e-425">程序</span><span class="sxs-lookup"><span data-stu-id="db12e-425">Procedures</span></span>  
  
-   <span data-ttu-id="db12e-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db12e-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="db12e-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db12e-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="db12e-428">檢視</span><span class="sxs-lookup"><span data-stu-id="db12e-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="db12e-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="db12e-429">Tables and Views</span></span>  
  
|<span data-ttu-id="db12e-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-430">ColumnName</span></span>|<span data-ttu-id="db12e-431">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="db12e-433">String</span><span class="sxs-lookup"><span data-stu-id="db12e-433">String</span></span>|  
|<span data-ttu-id="db12e-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-434">TABLE_OWNER</span></span>|<span data-ttu-id="db12e-435">String</span><span class="sxs-lookup"><span data-stu-id="db12e-435">String</span></span>|  
|<span data-ttu-id="db12e-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-436">TABLE_NAME</span></span>|<span data-ttu-id="db12e-437">String</span><span class="sxs-lookup"><span data-stu-id="db12e-437">String</span></span>|  
|<span data-ttu-id="db12e-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-438">TABLE_TYPE</span></span>|<span data-ttu-id="db12e-439">String</span><span class="sxs-lookup"><span data-stu-id="db12e-439">String</span></span>|  
|<span data-ttu-id="db12e-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-440">REMARKS</span></span>|<span data-ttu-id="db12e-441">String</span><span class="sxs-lookup"><span data-stu-id="db12e-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="db12e-442">資料行</span><span class="sxs-lookup"><span data-stu-id="db12e-442">Columns</span></span>  
  
|<span data-ttu-id="db12e-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-443">ColumnName</span></span>|<span data-ttu-id="db12e-444">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="db12e-446">String</span><span class="sxs-lookup"><span data-stu-id="db12e-446">String</span></span>|  
|<span data-ttu-id="db12e-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-447">TABLE_OWNER</span></span>|<span data-ttu-id="db12e-448">String</span><span class="sxs-lookup"><span data-stu-id="db12e-448">String</span></span>|  
|<span data-ttu-id="db12e-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-449">TABLE_NAME</span></span>|<span data-ttu-id="db12e-450">String</span><span class="sxs-lookup"><span data-stu-id="db12e-450">String</span></span>|  
|<span data-ttu-id="db12e-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-451">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-452">String</span><span class="sxs-lookup"><span data-stu-id="db12e-452">String</span></span>|  
|<span data-ttu-id="db12e-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-453">DATA_TYPE</span></span>|<span data-ttu-id="db12e-454">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-454">Int16</span></span>|  
|<span data-ttu-id="db12e-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-455">TYPE_NAME</span></span>|<span data-ttu-id="db12e-456">String</span><span class="sxs-lookup"><span data-stu-id="db12e-456">String</span></span>|  
|<span data-ttu-id="db12e-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="db12e-457">PRECISION</span></span>|<span data-ttu-id="db12e-458">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-458">Int32</span></span>|  
|<span data-ttu-id="db12e-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-459">LENGTH</span></span>|<span data-ttu-id="db12e-460">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-460">Int32</span></span>|  
|<span data-ttu-id="db12e-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="db12e-461">SCALE</span></span>|<span data-ttu-id="db12e-462">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-462">Int16</span></span>|  
|<span data-ttu-id="db12e-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-463">RADIX</span></span>|<span data-ttu-id="db12e-464">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-464">Int16</span></span>|  
|<span data-ttu-id="db12e-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-465">NULLABLE</span></span>|<span data-ttu-id="db12e-466">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-466">Int16</span></span>|  
|<span data-ttu-id="db12e-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-467">REMARKS</span></span>|<span data-ttu-id="db12e-468">String</span><span class="sxs-lookup"><span data-stu-id="db12e-468">String</span></span>|  
|<span data-ttu-id="db12e-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-470">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="db12e-471">程序</span><span class="sxs-lookup"><span data-stu-id="db12e-471">Procedures</span></span>  
  
|<span data-ttu-id="db12e-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-472">ColumnName</span></span>|<span data-ttu-id="db12e-473">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="db12e-475">String</span><span class="sxs-lookup"><span data-stu-id="db12e-475">String</span></span>|  
|<span data-ttu-id="db12e-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="db12e-477">String</span><span class="sxs-lookup"><span data-stu-id="db12e-477">String</span></span>|  
|<span data-ttu-id="db12e-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-479">String</span><span class="sxs-lookup"><span data-stu-id="db12e-479">String</span></span>|  
|<span data-ttu-id="db12e-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="db12e-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="db12e-481">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-481">Int16</span></span>|  
|<span data-ttu-id="db12e-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="db12e-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="db12e-483">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-483">Int16</span></span>|  
|<span data-ttu-id="db12e-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="db12e-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="db12e-485">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-485">Int16</span></span>|  
|<span data-ttu-id="db12e-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-486">REMARKS</span></span>|<span data-ttu-id="db12e-487">String</span><span class="sxs-lookup"><span data-stu-id="db12e-487">String</span></span>|  
|<span data-ttu-id="db12e-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="db12e-489">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="db12e-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="db12e-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="db12e-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-491">ColumnName</span></span>|<span data-ttu-id="db12e-492">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="db12e-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="db12e-494">String</span><span class="sxs-lookup"><span data-stu-id="db12e-494">String</span></span>|  
|<span data-ttu-id="db12e-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="db12e-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="db12e-496">String</span><span class="sxs-lookup"><span data-stu-id="db12e-496">String</span></span>|  
|<span data-ttu-id="db12e-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-498">String</span><span class="sxs-lookup"><span data-stu-id="db12e-498">String</span></span>|  
|<span data-ttu-id="db12e-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-499">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-500">String</span><span class="sxs-lookup"><span data-stu-id="db12e-500">String</span></span>|  
|<span data-ttu-id="db12e-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-501">COLUMN_TYPE</span></span>|<span data-ttu-id="db12e-502">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-502">Int16</span></span>|  
|<span data-ttu-id="db12e-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-503">DATA_TYPE</span></span>|<span data-ttu-id="db12e-504">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-504">Int16</span></span>|  
|<span data-ttu-id="db12e-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-505">TYPE_NAME</span></span>|<span data-ttu-id="db12e-506">String</span><span class="sxs-lookup"><span data-stu-id="db12e-506">String</span></span>|  
|<span data-ttu-id="db12e-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="db12e-507">PRECISION</span></span>|<span data-ttu-id="db12e-508">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-508">Int32</span></span>|  
|<span data-ttu-id="db12e-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-509">LENGTH</span></span>|<span data-ttu-id="db12e-510">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-510">Int32</span></span>|  
|<span data-ttu-id="db12e-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="db12e-511">SCALE</span></span>|<span data-ttu-id="db12e-512">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-512">Int16</span></span>|  
|<span data-ttu-id="db12e-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-513">RADIX</span></span>|<span data-ttu-id="db12e-514">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-514">Int16</span></span>|  
|<span data-ttu-id="db12e-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-515">NULLABLE</span></span>|<span data-ttu-id="db12e-516">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-516">Int16</span></span>|  
|<span data-ttu-id="db12e-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-517">REMARKS</span></span>|<span data-ttu-id="db12e-518">String</span><span class="sxs-lookup"><span data-stu-id="db12e-518">String</span></span>|  
|<span data-ttu-id="db12e-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="db12e-519">OVERLOAD</span></span>|<span data-ttu-id="db12e-520">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-520">Int32</span></span>|  
|<span data-ttu-id="db12e-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-522">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="db12e-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="db12e-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="db12e-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="db12e-524">ColumnName</span></span>|<span data-ttu-id="db12e-525">DataType</span><span class="sxs-lookup"><span data-stu-id="db12e-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="db12e-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="db12e-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="db12e-527">String</span><span class="sxs-lookup"><span data-stu-id="db12e-527">String</span></span>|  
|<span data-ttu-id="db12e-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="db12e-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="db12e-529">String</span><span class="sxs-lookup"><span data-stu-id="db12e-529">String</span></span>|  
|<span data-ttu-id="db12e-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="db12e-531">String</span><span class="sxs-lookup"><span data-stu-id="db12e-531">String</span></span>|  
|<span data-ttu-id="db12e-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-532">COLUMN_NAME</span></span>|<span data-ttu-id="db12e-533">String</span><span class="sxs-lookup"><span data-stu-id="db12e-533">String</span></span>|  
|<span data-ttu-id="db12e-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-534">COLUMN_TYPE</span></span>|<span data-ttu-id="db12e-535">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-535">Int16</span></span>|  
|<span data-ttu-id="db12e-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-536">DATA_TYPE</span></span>|<span data-ttu-id="db12e-537">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-537">Int16</span></span>|  
|<span data-ttu-id="db12e-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="db12e-538">TYPE_NAME</span></span>|<span data-ttu-id="db12e-539">String</span><span class="sxs-lookup"><span data-stu-id="db12e-539">String</span></span>|  
|<span data-ttu-id="db12e-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="db12e-540">COLUMN_SIZE</span></span>|<span data-ttu-id="db12e-541">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-541">Int32</span></span>|  
|<span data-ttu-id="db12e-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="db12e-543">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-543">Int32</span></span>|  
|<span data-ttu-id="db12e-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="db12e-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="db12e-545">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-545">Int16</span></span>|  
|<span data-ttu-id="db12e-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="db12e-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="db12e-547">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-547">Int16</span></span>|  
|<span data-ttu-id="db12e-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-548">NULLABLE</span></span>|<span data-ttu-id="db12e-549">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-549">Int16</span></span>|  
|<span data-ttu-id="db12e-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="db12e-550">REMARKS</span></span>|<span data-ttu-id="db12e-551">String</span><span class="sxs-lookup"><span data-stu-id="db12e-551">String</span></span>|  
|<span data-ttu-id="db12e-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="db12e-552">COLUMN_DEF</span></span>|<span data-ttu-id="db12e-553">String</span><span class="sxs-lookup"><span data-stu-id="db12e-553">String</span></span>|  
|<span data-ttu-id="db12e-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="db12e-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="db12e-555">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-555">Int16</span></span>|  
|<span data-ttu-id="db12e-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="db12e-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="db12e-557">Int16</span><span class="sxs-lookup"><span data-stu-id="db12e-557">Int16</span></span>|  
|<span data-ttu-id="db12e-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="db12e-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="db12e-559">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-559">Int32</span></span>|  
|<span data-ttu-id="db12e-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db12e-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="db12e-561">Int32</span><span class="sxs-lookup"><span data-stu-id="db12e-561">Int32</span></span>|  
|<span data-ttu-id="db12e-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="db12e-562">IS_NULLABLE</span></span>|<span data-ttu-id="db12e-563">String</span><span class="sxs-lookup"><span data-stu-id="db12e-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db12e-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db12e-564">See Also</span></span>  
 [<span data-ttu-id="db12e-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="db12e-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
