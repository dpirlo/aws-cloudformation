# Cloudformation

Este documento presenta una plantilla de cloudformation de AWS.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.

```bash
pip install foobar
```

## Características

```python
# Amazon Elastic Container Service (Amazon ECS) cluster.
Type: AWS::ECS::Cluster
CapacityProviders:
        - FARGATE_SPOT

# Watchdogs
Type: AWS::ElasticLoadBalancingV2::TargetGroup
HealthCheckIntervalSeconds: 30
HealthCheckProtocol: HTTP
HealthyThresholdCount: 3
UnhealthyThresholdCount: 3

#Listener
Type: AWS::ElasticLoadBalancingV2::Listener
Port: 80

#Security Group
Type: AWS::EC2::SecurityGroup
CidrIp: '0.0.0.0/0' ### ACA VA MI IP

# Requerimientos
Type: AWS::ECS::TaskDefinition
Cpu: 256
Memory: 512

# Características del sistema (Máximas instancias y mínimas)
  MinContainers:
    Type: Number
    Default: 1
    Description: How many copies of the service task to run, a minimum

  MaxContainers:
    Type: Number
    Default: 5
    Description: How many copies of the service task to run, at maximum

# Escalado
Type: AWS::ApplicationAutoScaling::ScalingPolicy
PredefinedMetricType: ECSServiceAverageCPUUtilization
TargetValue: 50 ##Supera 50% de uso de cpu e instancia otro container

```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[GPL](https://www.gnu.org/licenses/licenses.es.html)