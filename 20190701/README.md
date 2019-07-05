�Ǒf�l�� AWS + Docker + Rails�ŃV�X�e���\�z�����b�B

# �͂��߂�
�Â��悫EC2�̃I���v���̍\������AECS�\���ɏ悹������Č���S�������̂ŁA  
�����ō��������Ƃ͂܂�|�C���g�Ȃǂ��܂Ƃ߂܂��B

## ���s�T�[�r�X�\��

|����|���e|
| --- | --- |
|����|Ruby 2.4.0 |
|�t���[�����[�N|Ruby on Rails 5|
|�E�F�u�T�[�o |nginx|
|�f�[�^�x�[�X |MariaDB|
|���̑�|GitHubEnterprise|

## �Č��őΉ���������
### Ruby�̍X�V
2.6.2 �Ƀo�[�W�����A�b�v�B
### �R���e�i�Z�p�̗̍p
ECS+fargate�̍\���ō\�z�B
### CI/CD�������Ή�  
CircleCi�ACodePipeline�ACode3�Z��(CodeCommit,CodeBuild,CodeDeploy)�̓���

## ���C���̕M�҂̃X�L��
### �T�[�r�X�J��
�I���v��/AWS�ł̐V�KEC�T�[�r�X�̍\�z�o������  
### AWS
AWS��3����  
AWS�F�� �N���E�h�v���N�e�B�V���i�[ ����  
### ruby
�f�l
### �R���e�i/Docker
�f�l
###  CI/CD
�f�l�B
jenkins�ŃW���u��G�������Ƃ�������x�B

---

# �S��
�J���̐i�ߕ��Ƃ�  

## �܂��̓T���v���𓮂�����悤��
�n���Y�I�������Ȃǂ�ϋɓI�Ɋ��p���A�ŏ��ɓ��삷����̍���Ă���̏C���A�g���������߂��܂��B  
��b�I�ȕ���(VPC�A�T�u�l�b�g�A�Z�L�����e�B�O���[�v)�Ȃǂ�S�ۂ��Ă����̂ł͂܂�ǂ��낪����܂��B

## ����ł��������낤
�\�z�o���̂���L���ҁA�܂���AWS�����SA�ɋ��͈˗����āA����ł�������\�z���܂��傤�B  
�ςȂ͂܂��������ƁA����i�܂Ȃ��Ȃ�Ă��Ƃ����肦�܂��B  
�Y�񂾏�ő��k���Ă݂���A�u���͌����Ⴂ�ȏꏊ�𒲍����Ă����v�Ƃ������Ƃ��B   
���̍ۂ̒��ӓ_�Ƃ��āA�����l�̈ӌ������݂ɕ����Ă�ƍ������₷���ł��B  

## �H���̌��ς���
���m�Ȍ��ς��肪�Ђ悤�ȏꍇ�́A������Ȃ����Ƃ��o���邾�����Ȃ����܂��傤�B
������Ȃ����Ƃ������ƌ�������Ɏ��Ԃ�����܂��B  
������Ȃ����̂̐������A���肷��H�����{�ł͂Ȃ���Z�����Ǝv���Ă��������B
�G���[�������������I�ɔ��������ꍇ�ɂ́A���_�I�ɂ����Ȃ�܂��B  

---

# AWS��
## IAM
### AWS���[�g�A�J�E���g 
�A�J�E���g�̕������j���������܂��傤�B  
1�A�J�E���g�ŕ����̃V�X�e�����Ǘ����悤�Ƃ���ƁA�����ȂǂŔ��ɕ�����ɂ����Ȃ�܂��B  
�؂蕪���闱�x�Ƃ��ẮA�����P�ʁA�V�X�e���P�ʁA���P�ʂȂǂɂȂ�Ǝv���܂��B  

### �F�؏��
�`�[���p�̋��ʃA�J�E���g�����܂��傤�B
�l�̃��[�U���甭�s����ƁA���C������ސE�����Ƃ���ID���폜����ē����Ȃ��Ȃ邱�Ƃ�����܂��B

### �|���V�[�̍č쐬�����ɃG���[
CodeBuild�Ŕ����������A�ȉ��̋L�����Q�Ƃ��Ă��Ή������B

```
The policy is attached to 0 entities but it must be attached to a single role
https://qiita.com/kyuaz/items/3da93bd05b1342212577
```

## VPC
VPC���ŕ����T�u�l�b�g���\�z����̂ŁA�傫�߂ɂƂ�܂��傤�B  
VPC��CIDR��/24�Ŋm�ۂ����IP���̂��̂��s�����邩�A������ɂ���IP�тɂȂ�܂��B

### �T�u�l�b�g
�����Z�O�����g�ƊO���Z�O�����g�𕪊����܂��傤�B

### ���[�e�B���O private subnet����O�ɐڑ��ł��Ȃ�
EIP�Anatgw��igw�A���[�g�e�[�u���̐ݒ���m�F���܂��傤

###  DNS�o�^�ASSL�ؖ������s
route53��A���R�[�h�AC���R�[�h�̓o�^�A
ACM�̏ؖ������s��AWS�̃T�|�[�g�Ƀz���C�g���X�g�ɈϔC�ݒ肪�K�v�ȏꍇ������܂��B

## EC2
����m�F�p��EC2���쐬���Ă����Ƃ悢�B���̐؂蕪���Ɏg���܂��B

## ALB
ALB��������Z�O�����g�ɗ����Ƃ��́A80�ԃ|�[�g�ŒʐM���悤�B
������SSL�ؖ�����ݒ肷��K�v���Ȃ��Ȃ邼�B

## RDB
�f�t�H���g�l���ƁAtimezone��UTC�ƂȂ��Ă��邽�ߓ��{���ԂƂ͎���������܂��B
�p�����[�^�O���[�v�̐V�K�쐬�A�p�����[�^�̍X�V�A���蓖�ĂƔ��l��RDB�ċN�����K�v�ɂȂ邽�߁A�����^�C�~���O�ŏC������Ƃ悢�ł��B

## S3
GUI����o�P�b�g���R�s�[�����Ă��AAWS�o�P�b�g�|���V�[�܂ł̓R�s�[����Ȃ��B

# ECS	
## ���O�̏o�͐�ɂ���
������R���e�i��ɏo�͂��Ă��郍�O�́A�R���e�i�폜���Ă��܂��Ə����܂��B  
�v���ɂ���ẮA�o�͐��S3�ȂǂɕύX���܂��傤�B

## �f�o�b�O���ɂ���
Fargate�͋N���R���e�i�ւ�SSH���O�C���Ȃǂ͂ł��Ȃ��ł��B  
���[�J���J������p�ӂ��邩�A�J������p�ӂ���SSH�ڑ��ł���EC2��I�����܂��傤�B

---

# �R���e�i/Docker��

## docker images apline 
���O�C���V�F�� bash�ł͂Ȃ�ash�B
```
#��������
docker run --rm -it test-image bash
```
## ����Docker image�̎���
docker build���ɕK�v�ȃ\�t�g�E�G�A�̃C���X�g�[�����L�ڂ��邱�Ƃ�����Ǝv���܂��B
�Â�ubuntu�C���[�W���g���Ă���ƁAapt-get�ŃG���[���o��悤�ɂȂ���
�����̓~���[�T�C�g����̍폜���ꂽ���߁B
https://gihyo.jp/admin/clip/01/linux_dt/201903/25
�Ή��Ƃ��ẮAOS�o�[�W�������グ�邱�ƂőΉ����܂����B
���p���Ă���OS�̃T�|�[�g�����������ӎ����Ă����Ƃ悢�ł��B

## docker-compose�̈Ⴂ
���������́ADockerfile������ECS+fargate���\�z�ł���Ǝv���Ă��܂������A
docker-compose������Ă�����ECS�^�X�N��`�Ɏ��Ă��邽�߈ڍs���₷���̂ł����߂��܂��B

## �ꕔGem���C�u�����������Ȃ��Ȃ�\��������
�t�����g�p�̃��|�W�g����docker run�����Ƃ���A���̃G���[�������B  
```mini_racer_extension.so: undefined symbol: ```   
�����������A�������@���݂����Ȃ������̂ŁAalpine��gem�̑������Ƃ������f�������B
�Ή��Ƃ��āAalpine��f�O���ĕʂ�docker image�𗘗p���܂����B

---

# ruby��

## �\�P�b�g�ɂ���
config�Ƀ\�P�b�g��`���o���܂����Anginx�𗧂Ă�ꍇ�ł��B  
docker�ł͂�������nginx���s�v�ɂȂ邽�߃\�P�b�g�̒�`���s�v�ɂȂ�܂��B


ALB�ō\���ł� �s�v����I�I
ALB������̂�enginx�R���e�i������Ă��܂��B
�R���e�i��ECS�Ŏ��s����ꍇ�A�f�[���i�C�Y���[�h����exit 0 ����B


---

# CICD��
CICD
	circleci
	yaml�C���f���g

	circleci�ł͑Θb���[�h���ƂƂ܂�
	
	������	"�V�X�e���\��
	CICD AWS �ǂ���db:migrate���s���邩�l�����K�v�B
	AWS�O��CICD�c�[������db:migrate�����s���悤�Ƃ���ƁA
	�C���^�[�l�b�g����A�N�Z�X�ł���悤�����J����K�v������"
	
	codecommit
	circleci	���|�W�g�����Q����Ƃ������Ƃ́A�ʂɃR�~�b�g����ƁA�s��v���N����B

	������	rails docker	12 factor��git flo�ƁA�̍����̂��񂪂��^
	���߂Ă������ق���������I

	���Ƃ��Η^����l���ς���Ă���

������	rails docker	�\���ɉe������@SECRET_KEY_BASE
������	rails docker	12 factor��git flo�ƁA�̍����̂��񂪂��^

