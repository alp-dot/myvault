---
title: "Pytest Test Loader Guide"
source: "https://gemini.google.com/app/8a1f97ed6bca6451"
author:
  - "[[Gemini]]"
published:
created: 2024-12-31
description: "Comprehensive guide to pytest test loader and test collection rules"
tags:
  - "python"
  - "testing"
  - "pytest"
---

pytestのテストローダーは、以下の条件でテストファイルを収集し、テストを実行します。

**1\. ファイル名:**

- `test_*.py` または `*_test.py` という名前のファイルを探します。
- これらのファイルは、テスト対象のコードと同じディレクトリ、またはそのサブディレクトリに配置する必要があります。

**2\. テスト関数/メソッド名:**

- `test_` で始まる関数またはメソッドをテストとして認識します。
- テストクラスは `Test` で始まる必要があります (ただし、`unittest.TestCase` を継承する場合はこの規則は適用されません)。

**3\. ディレクトリ:**

- `__init__.py` ファイルを含むディレクトリをパッケージとして認識し、その中のテストファイルも収集します。
- `conftest.py` という名前のファイルは、テストの設定やフィクスチャを定義するために使用されます。このファイルは、テストファイルが置かれているディレクトリ、またはその親ディレクトリに配置することができます。

**4\. コマンドラインオプション:**

- `-k` オプションで、特定のキーワードを含むテストだけを実行することができます。
- `-m` オプションで、特定のマーカーが付いたテストだけを実行することができます。
- `-x` オプションで、最初のエラーが発生したらテストを停止することができます。

**5\. プラグイン:**

- pytestはプラグインによって機能を拡張することができます。
- プラグインは、テストの収集方法や実行方法を変更することができます。

**例:**

```
# test_example.py

def test_addition():
  assert 1 + 1 == 2

def test_subtraction():
  assert 2 - 1 == 1
```

この例では、`test_example.py` というファイルに `test_addition` と `test_subtraction` という2つのテスト関数が定義されています。pytest はこれらの関数をテストとして認識し、実行します。

**補足:**

- pytest は、`unittest.TestCase` を継承したテストクラスも実行することができます。
- pytest は、doctest を使用して、docstring に埋め込まれたテストを実行することもできます。

pytest のテストローダーは、これらの条件に基づいてテストを収集し、実行します。これらの条件を理解することで、効率的にテストを作成し、実行することができます。