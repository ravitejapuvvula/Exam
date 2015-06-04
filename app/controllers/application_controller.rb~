class ApplicationController < ActionController::Base
  # Prevent CSRF attacks by raising an exception.
  # For APIs, you may want to use :null_session instead.
    
  protect_from_forgery with: :exception
  before_action :authenticate_user!

  private
  def check_permission
    if user_signed_in?
      
      current_user.role == "Admin"
      	
     
    end
  end
end
