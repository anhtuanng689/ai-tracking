# Tracking
## Câu 1: Exact Inference Observation
Duyệt từng vị trí nếu noisyDistance là none thì pacman đã ăn ma và cập nhật vị trí ma bị ăn. Nếu không thì cập nhật belief dựa vào khoảng cách từ ma đến vị trí đó.
## Câu 2: Exact Inference with Time Elapse
Duyệt để lấy phân phối về vị trí ma sẽ đến tiếp theo và cập nhật belief.
## Câu 3: Exact Inference Full Test
Duyệt các action, lấy vị trí của trạng thái kế tiếp, duyệt vị trí của ma livingGhostPositionDistributions, lấy vị trí của ma có khả năng cao nhất và tính khoảng cách nếu vị trí đó khác 0 rồi cập nhật giá trị value cho action đó.
## Câu 4: Approximate Inference Observation
- initializeUniformly(self, gameState): liệt kê các vị trí của con ma có thể có và thiết lập các vị trí cụ thể.
- getBeliefDistribution(self): lấy beliefDistribution bằng Couter().
- observe(self, observation, gameState):
  + Nếu noisyDistance là none thì cập nhật vị trí particle là vị trí ma bị ăn.
  + Nếu không, cập nhật belief.
## Câu 5: Approximate Inference with Time Elapse
Hàm elapseTime như câu 2: lấy tất cả các vị trí của ma và mẫu vị trí cho 1 số particle.
## Câu 6: Joint Particle Filter Observation
- initializeParticles(self): liệt kê tất cả những vị trí hợp lệ rồi tráo.
- getBeliefDistribution(self): duyệt từng particle trong self.particles với mỗi giá trị beliefDistribution[particle] cộng thêm 1.0.
- observeState(self, gameState): Nếu số noisyDistances < số ma với mỗi particleIndex trong range(self.numParticles) và duyệt ma trong range(self.numGhosts):
  + Nếu noisyDistance là none thì ma sẽ xuất hiện trong ô tù.
  + Nếu không, cập nhật lại belief cho mỗi ma.
## Câu 7: Joint Particle Filter with Elapse Time
Lấy phân bố vị trí đã cho và thêm newParticle mẫu lấy từ phân bố vị trí đó.
