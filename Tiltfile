# Tiltfile

# Function to create namespace for all worker nodes
def demo_create_namespace_service():
    k8s_yaml('./local-cicd-manifests/demo-namespace.yml')

# Function to build and deploy: liquibase update for mssqldb service
def demo_update_mssqldb_service():
    # Build from Dockerfile
    docker_build('demo-update-mssqldb', context='./src/db/', dockerfile='./src/db/Dockerfile')
    # Specify the Kubernetes manifest for the deployment
    k8s_yaml('./local-cicd-manifests/demo-update-mssqldb.yml')
    # Assign port
    k8s_resource('demo-update-mssqldb', 
    port_forwards=5432,
    labels="database")

# # Function to build and deploy:BFF service
def demo_bff_blog_service():
    # Build from Dockerfile
    docker_build('demo-bff-web-blog',
                 context='./src/bff-blog',
                 dockerfile='./src/bff-blog/Dockerfile')
    # Specify the Kubernetes manifest for the API deployment
    k8s_yaml('./local-cicd-manifests/demo-bff-web-blog.yaml')
    # Assign port
    k8s_resource('demo-bff-web-blog',
                 port_forwards=['8081:8080','5005:5005'],
                 resource_deps=['demo-mssqldb','demo-update-mssqldb'],
                 labels="service",
                 trigger_mode=TRIGGER_MODE_MANUAL)

demo_create_namespace_service()
demo_update_mssqldb_service()
demo_bff_blog_service()