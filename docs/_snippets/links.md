{%- set urls =
  {
    'repo': {
      'url': 'https://github.com/bjw-s/k8s-gitops'
    },
    'external': {
      'ansible': {
        'url': 'https://www.ansible.com/',
        'label': 'Ansible'
      },
      'ansible-role-k3s': {
        'url': 'https://github.com/PyratLabs/ansible-role-k3s'
      },
      'calico': {
        'url': 'https://docs.projectcalico.org/about/about-calico'
      },
      'cert-manager': {
        'url': 'https://cert-manager.io'
      },
      'coredns': {
        'url': 'https://github.com/coredns/coredns',
        'label': 'CoreDNS'
      },
      'external-dns': {
        'url': 'https://github.com/kubernetes-sigs/external-dns'
      },
      'flux': {
        'url': 'https://fluxcd.io'
      },
      'k3s': {
        'url': 'https://k3s.io'
      },
      'kah_repo_awesome': {
        'url': 'https://github.com/k8s-at-home/awesome-home-kubernetes',
        'label': 'awesome-home-kubernetes'
      },
      'kah_discord': {
        'url': 'https://discord.gg/sTMX7Vh',
        'label': 'k8s@home Discord'
      },
      'kasten': {
        'url': 'https://www.kasten.io',
        'label': 'Kasten K10'
      },
      'kube-vip': {
        'url': 'https://kube-vip.io'
      },
      'letsencrypt': {
        'url': 'https://letsencrypt.org',
        'label': 'LetsEncrypt'
      },
      'metallb': {
        'url': 'https://metallb.universe.tf'
      },
      'multus': {
        'url': 'https://github.com/k8snetworkplumbingwg/multus-cni',
        'label': 'Multus'
      },
      'rook-ceph': {
        'url': 'https://rook.io'
      },
      'sops': {
        'url': 'https://github.com/mozilla/sops',
        'label': 'Mozilla SOPS'
      }
    }
  }
-%}

{% macro external(name, label) -%}
  {% if label %}
  [{{ label }}]({{ urls.external[name].url }}){target=\_blank}
  {% elif urls.external[name].label %}
  [{{ urls.external[name].label }}]({{ urls.external[name].url }}){target=\_blank}
  {% else %}
  [{{ name }}]({{ urls.external[name].url }}){target=\_blank}
  {% endif %}
{%- endmacro %}

{% macro repoUrl(label, suffix) -%}
  [{{ label }}]({{ urls.repo.url }}{% if label %}/{{ suffix }}{% endif %}){target=\_blank}
{%- endmacro %}