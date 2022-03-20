# terraform-cloud
# the below lines are my main.tf files
resource "aws_vpc" "myVpc" {
  cidr_block = var.myVpc_cidr
  tags = {
    "Name" = "myVpc"
  }
}
resource "aws_subnet" "mySubnet" {
  vpc_id            = aws_vpc.myVpc.id
  cidr_block        = var.mySubnet_cidr
  availability_zone = var.my_Az
  tags = {
    "Name" = "mySubnet"
  }
}


# the below lines are my var.tf files
variable "myVpc_cidr" {
    description = "cidr for myvpc"
      type = string
    default = "10.0.0.0/16"
}

variable "mySubnet_cidr" {
    description = "cidr for mysubnet"
    type = string
    default = "10.0.0.0/24"
}

variable "my_Az" {
    description = "my subnet Az"
  type = string
  default = "us-east-1a"
}
