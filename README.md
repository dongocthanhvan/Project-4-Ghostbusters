# 2021l_INT3401_8_Pacman_Tracking
SOLUTION FOR PACMAN - TRACKING ASSIGNMENT:

Question 1: 
Xác suất ở mỗi vị trí mà ma có thể xuất hiện được tính bằng tích xác suất hậu nghiệm của tiếng ồn nhân với xác suất tiên nghiệm mà ma xuất hiện ở mỗi vị trí (được cho bởi phân phối đều):

      allPossible[p] = emissionModel[trueDistance] * self.beliefs[p]
                                                  
Question 2: 

Xác suất mà ma xuất hiện ở vị trí tiếp sẽ bằng xác suất ở vị trí hiện tại nhân với xác suất mà ma sẽ xuất hiện ở các vị trí tiếp theo. Hoặc có thể hiểu đây là xác suất có điều kiện P(vị trí tiếp theo | vị trí hiện tại của ma) và ta sẽ cập nhật xác suất này:

    for newPos, probability in positionDist.items():
      newBeliefs[newPos] += probability * self.beliefs[oldPos]
                                                                                                        
Question 3:

Tìm ra vị trí có khả năng xuất hiện nhất của mỗi ma và khoảng cách từ pacman đến những vị trí đó. Sau đó tìm ra vị trí của ma gần nhất và khoảng cách từ pacman đến đó. Cuối cùng chọn ra action tốt nhất:

    bestNewDistance = float('inf')
          bestAction = []
          for action in legal:
              successorPosition = Actions.getSuccessor(pacmanPosition, action)
              newDistance = self.distancer.getDistance(closestPosition, successorPosition)
              if newDistance < bestNewDistance:
                  bestNewDistance = newDistance
                  bestAction = [action]
              elif newDistance == bestNewDistance:
                  bestAction.append(action)
          return random.choice(bestAction)
          
Question 4: 
Khác Question 1 ở chỗ sử dụng tập mẫu để đưa ra suy diễn
Hàm getBeliefDistribution(): Khởi tạo xác suất cho mỗi vị trí trong tập particles là bằng nhau và tổng bằng 1 (phân phối đều)
Hàm observe(): Tương tự hàm observe() của Question 1:
Khởi tạo lại tập mẫu nếu như xác suất ở tất cả các vị trí đều bằng 0



                                                  
