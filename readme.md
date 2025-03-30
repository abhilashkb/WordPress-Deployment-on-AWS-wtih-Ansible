wordpress-aws/
├── inventory/
│   └── hosts.ini
├── group_vars/
│   └── all.yml
├── roles/
│   ├── ec2_provision/
│   │   ├── tasks/
│   │   │   └── main.yml
│   │   └── defaults/
│   │       └── main.yml
│   ├── nginx_setup/
│   │   ├── tasks/
│   │   │   └── main.yml
│   │   ├── handlers/
│   │   │   └── main.yml
│   │   └── templates/
│   │       ├── nginx.conf.j2
│   │       └── wordpress.conf.j2
│   └── wordpress_setup/
│       ├── tasks/
│       │   └── main.yml
│       └── defaults/
│           └── main.yml
└── site.yml