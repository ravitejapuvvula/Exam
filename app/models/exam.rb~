class Exam < ActiveRecord::Base
 
  has_many :questions, :dependent => :destroy
  accepts_nested_attributes_for :questions, :reject_if => lambda { |a| a[:content].blank? }, :allow_destroy => true

 attr_writer :current_step

validates_presence_of :name, :if => lambda { |o| o.current_step == "exam" }

def current_step
  @current_step || steps.first
end

def steps
  %w[Enter Exam]
end

def next_step
  self.current_step = steps[steps.index(current_step)+1]
end

def previous_step
  self.current_step = steps[steps.index(current_step)-1]
end

def first_step?
  current_step == steps.first
end

def last_step?
  current_step == steps.last
end

def all_valid?
  steps.all? do |step|
    self.current_step = step
    valid?
  end
end

end
