# machine-learning-project
01.112 Machine Learning Design Project

Group member: Gao Yiming 1002180, Li Xueqing 1002182, Zang Xueqing 1002185

Instruction: 
For Part2&4, just run the ipynb file.
For Part3&5, there is no evaluation code in the file. You may add the following code
to get evaluation results:

for lan in ["CN", "EN", "SG", "FR"]:
    
    with open(lan + '/dev.p3.out' ) as f:
    #with open(lan + '/dev.p5.out' ) as f:
    
        pred = get_entities(f)
        
    with open(lan + '/dev.out' ) as f:
    
        gold = get_entities(f)
        
    print(lan)
    
    compare_result(gold, pred)
