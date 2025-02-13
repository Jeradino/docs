---
title: アクション
intro: 'With the Actions API, you can manage and control {% data variables.product.prodname_actions %} for an organization or repository.'
redirect_from:
  - /v3/actions
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - API
miniTocMaxHeadingLevel: 3
---


{% data variables.product.prodname_actions %} API では、REST API を使用して {% data variables.product.prodname_actions %} を管理できます。 {% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} require the permissions mentioned in each endpoint. 詳しい情報については、「[{% data variables.product.prodname_actions %} のドキュメント](/actions)」を参照してください。

{% for operation in currentRestOperations %}
  {% unless operation.subcategory %}{% include rest_operation %}{% endunless %}
{% endfor %}

## 成果物

成果物 API では、ワークフローの成果物に関する情報をダウンロード、削除、および取得できます。 {% data reusables.actions.about-artifacts %} 詳しい情報については、「[成果物を利用してワークフローのデータを永続化する](/actions/automating-your-workflow-with-github-actions/persisting-workflow-data-using-artifacts)」を参照してください。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'artifacts' %}{% include rest_operation %}{% endif %}
{% endfor %}

{% ifversion fpt or ghes > 2.22 or ghae or ghec %}
## 権限

The Permissions API allows you to set permissions for what enterprises, organizations, and repositories are allowed to run {% data variables.product.prodname_actions %}, and what actions are allowed to run.{% ifversion fpt or ghec or ghes %} For more information, see "[Usage limits, billing, and administration](/actions/reference/usage-limits-billing-and-administration#disabling-or-limiting-github-actions-for-your-repository-or-organization)."{% endif %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'permissions' %}{% include rest_operation %}{% endif %}
{% endfor %}
{% endif %}

## シークレット

シークレット API では、暗号化されたシークレットに関する情報を作成、更新、削除、および取得できます。 {% data reusables.actions.about-secrets %} 詳しい情報については、「[暗号化されたシークレットの作成と利用](/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)」を参照してください。

{% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} must have the `secrets` permission to use this API. 認証されたユーザは、シークレットを作成、更新、または読み取るために、リポジトリへのコラボレータアクセス権を持っている必要があります。

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'secrets' %}{% include rest_operation %}{% endif %}
{% endfor %}

## セルフホストランナー

{% data reusables.actions.ae-self-hosted-runners-notice %}

セルフホストランナー API では、自分のホストランナーの登録、表示、削除ができます。 {% data reusables.actions.about-self-hosted-runners %} 詳しい情報については「[自分のランナーのホスト](/actions/hosting-your-own-runners)」を参照してください。

{% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} must have the `administration` permission for repositories the `organization_self_hosted_runners` permission for organizations. Authenticated users must have admin access to repositories or organizations, or the `manage_runners:enterprise` scope for enterprises to use this API.

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'self-hosted-runners' %}{% include rest_operation %}{% endif %}
{% endfor %}

## セルフホストランナーグループ

{% data reusables.actions.ae-self-hosted-runners-notice %}

セルフホストランナーグループ API を使用すると、セルフホストランナーのグループを管理できます。 詳しい情報については、「[グループを使用したセルフホストランナーへのアクセスを管理する](/actions/hosting-your-own-runners/managing-access-to-self-hosted-runners-using-groups)」を参照してください。

{% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} must have the `administration` permission for repositories or the `organization_self_hosted_runners` permission for organizations. Authenticated users must have admin access to repositories or organizations, or the `manage_runners:enterprise` scope for enterprises to use this API.

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'self-hosted-runner-groups' %}{% include rest_operation %}{% endif %}
{% endfor %}

## ワークフロー

ワークフロー API を使用すると、リポジトリのワークフローを表示できます。 {% data reusables.actions.about-workflows %}詳しい情報については、「[GitHub Actions でワークフローを自動化する](/actions/automating-your-workflow-with-github-actions)」を参照してください。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'workflows' %}{% include rest_operation %}{% endif %}
{% endfor %}

## ワークフロージョブ

ワークフロージョブ API では、ログとワークフロージョブを表示できます。 {% data reusables.actions.about-workflow-jobs %}詳しい情報については、「[GitHub Actions のワークフロー構文](/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions)」を参照してください。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'workflow-jobs' %}{% include rest_operation %}{% endif %}
{% endfor %}

## ワークフロー実行

ワークフロー実行 API では、ワークフロー実行のログを表示、再実行、キャンセル、表示できます。 {% data reusables.actions.about-workflow-runs %}詳しい情報については、「[ワークフロー実行を管理する](/actions/automating-your-workflow-with-github-actions/managing-a-workflow-run)」を参照してください。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'workflow-runs' %}{% include rest_operation %}{% endif %}
{% endfor %}
